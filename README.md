# Cool Papers Summary on Generative AI
We know that generative AI is booming like craxy and with all its publication it is really tough to go through all the cool research. (Atleast for me it is impossible). There are some cool twitter handles that keeps you updated about the cool work, I will mention some of them here.

I am creating this repo to consolidate all the work that is happening in Generative AI ( diffusion or LLMs) in one repository. I will personally try to add the summary of the papers that I have read. I recommend everyone who is an active reader to write up small summary about the paper that you have read and share it with everyone. This will be a cool reading group. 

## 1. Self-Consuming Generative Models Go MAD (https://arxiv.org/pdf/2307.01850.pdf)
With all the growing power of generative models and the number of generative images online are adding up to our training data for future training. But using those images in our training set even useful ?? The paper kind of shows that this actually degrades the model performance with increasing number of generation. 

> Our primary conclusion across all scenarios is that without enough fresh real data in each generation of an autophagous("self-consuming") loop, future generative models are <strong>doomed to have their quality (precision) or diversity (recall) progressively decrease.</strong>

> Repeated training with synthetic data might progressively amplify the biases and artifacts present in any generative model. We hypothesize that synthetic data contains fingerprints of the generator architecture (e.g., convolutional traces [40] or aliasing artifacts [41]) that may be reinforced by self-consuming generators.

They also experiment with different portion of synthetic data in the training data with generation. 
1. Fully synthetic loop : training dataset for each generation’s model consists solely of synthetic data sampled from previous generations’ models.
2. Synthetic Augmentation : training dataset consist of fixed real data plus images from previous generation model as augmentation.
3. Fresh data : training dataset for each generation’s model consists of a combination of synthetic data sampled from previous generations’ models plus a fresh set of real training data.

> Sampling bias :  Users of generative models tend to manually curate (“cherry-pick”) their synthetic data, preferring high-quality samples and rejecting low-quality ones. Moreover, state-of-the-art generative models typically feature controllable parameters that can increase synthetic quality at the expense of diversity [42, 58]. We demonstrate that the sampling biases induced through such quality-diversity (precision-recall) trade-offs have a major impact on the behavior of an autophagous training loop. Specifically, we show that, without sampling bias, autophagy can lead to a rapid decline of both quality and diversity, whereas, with sampling bias, quality can be maintained but diversity degrades even more rapidly.


Findings:
> <strong> Fresh data </strong> : In fresh data loop we see that a large amount of synthetic data hurts performance, while a modest amount of synthetic data actually boosts performance.

> <strong> Fully synthetic loop </strong> : Training generative models exclusively on synthetic data in a fully synthetic loop without sampling bias reduces both the quality and diversity of their synthetic data decreases over generations.

> <strong> Fully synthetic loop </strong> : Training generative models on high-quality synthetic data(with sampling bias) always produces a loss in either synthetic quality or synthetic diversity. Boosting synthetic quality penalizes synthetic diversity.

> <strong> Synthetic Augmentation </strong> : Training generative models in a synthetic augmentation loop with both fixed real and synthetic training data without sampling bias reduces both the quality and diversity of their synthetic data over generations, albeit more slowly than in fully synthetic loop case.

> <strong> Synthetic Augmentation </strong> : When incorporating real data in the synthetic augmentation loop, even sampling bias cannot prevent increases in FID over generations.

This paper kind of proves that if you ought to use data from the pretrained generative models online then it might be harmful. Personally I have seen many some work using LLM to create training data. 

## 2. Challenges and Applications of Large Language Models(https://arxiv.org/pdf/2307.10169.pdf)
This is a survey paper on LLMs which discusses mainly challenges and application of LLMs. 

General Knowledge: 
- Models like GPT-4 and Claude can handle context windows of up to 32k and 100k tokens, respectively, equating to approximately 20k words or 40 pages of text. However, the cost of execution rises with the number of tokens used, hence the need for an efficient retriever to find the most relevant documents.
-  

Challenges:
1. The very large amount of training dataset has made it impossible for individual to read and conduct quality assesments n the encompassed documents thoroughly.
 - Near-Duplicates : This has been reported to degrade model performance.
 - Overlap with the test data
2. The goal of tokenizer is to handle rare and out-of-vocabulary words in a model’s vocabulary effectively while maintaining a limited number of tokens per sequence in the interest of computational complexity. But it comes with drawbacks:
   - Number of tokens necessary to convey same information varies significantly across language.
   - The embedding layer and output layer of LLM involve vocab size making up to 66% of the model parameter count.


## 3. On the Exploitability of Instruction Tuning (https://arxiv.org/pdf/2306.17194.pdf)
