## MOE and BitNet1.58


Is bigger better?- They key is DATA.

I received an interesting question from my colleagues and also my boss. “Can we build a small model with 1bit (Quantization to 1bit) and achieve the same performance as GPT3 and GPT4? - very large models”

 It's understandable because our small enterprise can’t host LLMs the size of GPT-3.5 or 4 in-house due to the significant time and cost involved in computational processing. Interestingly, we found that performing computational processes on an FPGA ( special chip)  is more efficient than using a GPU.  This would lower cost and engineering consumption.

Let's look at the conversations about this topic; generally speaking, it seems bigger is better, which is proven by the superiority of GPT-3 over GPT-2 and other predecessors [ref:)]. However, if we want to do a particular task well, like chatbots in the case of ChatGPT (GPT-3.5-turbo), then the data focus and the appropriate training procedure are of far greater importance. Smaller seems better. ( This follows the Scaling Laws for Neural Language Models.

Coming back to the question: “Can we achieve answer generation, understanding, and thinking capabilities similar to those of GPT-3.5 or 4 with a 1bitLLM?”

The answer is probably YES, at least "about" the inference performance, and many companies are doing this job: 

- Zephyr Beta 7B (based on Mistral with MOE architectures - a startup with $2B)has been fine-tuned on just ~300k chat data yet surpasses Llama-70B.
- Orca [4] (Microsoft) is small-sized and has its own reasoning training dataset, so it can have performance similar to GPT 4 at reasoning tasks.
- BitNet1.58 [5] can reduce the network to 1bit computation while maintaining the quality.

So, we must find a method to combine them and train them with many "domains”—data is a key. I believe the workflow should be similar to my figure.


P/S: I implemented a simple demo with  MOE- PEFT and BitNet to prove the ideas ( 1.58bit models can perform similarly on several tasks - e.g. Image Classification). The source code here: 


[1] Scaling Laws for Neural Language Models  https://arxiv.org/pdf/2001.08361.pdf]
[2] Mixture-of-LoRAs : https://arxiv.org/pdf/2403.03432.pdf
[3] MOE https://github.com/mistralai/mistral-src
[4] Orca https://arxiv.org/pdf/2306.02707.pdf
[5] BitNet158: https://www.linkedin.com/pulse/1bit-llm-small-still-large-bitnet158-gurneet-singh-tj3tc/
