## Notebooks to Fine-Tune LLMs on Instruction dataset

The recent developments in the field if NLP can be attributed to LLMS.
LLMs coined Large Language Models are models with Billions of parameters trained on massive data from the internet.
Although these models show execptional knowledge and various emergent properties due to their scale, they are not aligned for human conversations.
To align LLMs to Human preferences we fine-tune them on guess what , 'Human preferences' !!
Various techniques are applied to make them respond well to human instructions, techniques like RLHF, SFT and DPO are popular.


This repo contains notebooks to finetune an LLM on publicly available preference datasets.


#### What models do we choose?

You can choose any models that can be trained on your available system (you need enough GPU VRAM).
Me being GPU Poor (yes that is a title now-a-days) have choosen Microsoft Research's baby [Phi-2](https://www.microsoft.com/en-us/research/blog/phi-2-the-surprising-power-of-small-language-models/). 


They call this model and its predecessors as SLMs or Small Language models due to their comparably small size of around 1.5 ~ 3 Billion parameters.
These models are trained on what they call Textbook grade data with lots of attention on 'quality' of the data instead of quantity. 
The results show that these models surpass the current SOTA open models on tasks like Reasoning, Math or Coding right out of the box. 


Although trained on higher quality data these models are not trained to follow human instructions, so I have tried to train them on the famous Stanford [Alpaca](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwiJif6Xm_CEAxWd3TgGHZJlAcEQFnoECBUQAQ&url=https%3A%2F%2Fcrfm.stanford.edu%2F2023%2F03%2F13%2Falpaca.html&usg=AOvVaw1gqeYCEcNMsRfLb9aOGD2S&opi=89978449) instruction dataset sampled by prompting ChatGPT.


### What is DPO ?
[DPO](https://arxiv.org/pdf/2305.18290.pdf) or Direct Preference Optimization is a techinque that uses the Language model itself as an implicit reward model to align to Human preferences. After tuning the model initially with SFT (Supervised Fine Tuning), we need the model to incorporate Human Feedback to generate quality and coherent responses. 


To do this a technique called PPO (Proximal Policy approximation) is used. This is a RL algorithm that updates the policy based on feedback provided by Human Annotators. This technique can be expensive (due to Humans in the loop) and unstable. To tackle this DPO was proposed.

DPO formulates the PPO objective to implicitly model the optimal reward and use an offline dataset of Human Feedback. Due to this we can choose from hundreds of publicly available datasets containing Human feedback and train our baby Phi to follow Human preferences !



