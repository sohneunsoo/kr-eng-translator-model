# 번역기 + 논문 모델 구현

## Text 전처리
korean
- okt morphs
- with stem -  결과 약간 떨어짐 (random sample이 달라서 일수도 있음)

english
- 기본 tokenizer
  
25 token 이상 문장 빼기  
Korean  
![krtoken](https://github.com/sohneunsoo/kr-eng-translator-model/assets/121411251/c6658150-b5c7-42a5-aeab-0b0be0aa8e51)  
English  
![engtokens](https://github.com/sohneunsoo/kr-eng-translator-model/assets/121411251/7fc58b81-3d58-41c0-9baf-02df583468a6)


## 논문 모델

2 bidirectional+lstm -> 2 lstm  + attention

ref:


 Effective approaches to attention-based neural machine translation -2015 Luong
 
-4.5M sentence pairs dataset #limit vocab- top 50k, rest <unk> #filter sentences length under 50words #shuffle

-4layers- each 1000cells #1000dim_emb #lsdm dropout 0.2

-local attention- windowsize 10 #useful for long seq eg paragraphs/documents

-parameters uniformly initialized [-0.1,0.1]

-SGD (adam introduced same year 2015)  #minibatchsize128 #normalized gradient learning_rate schedule- start_lr=1, 12epochs, start halving after 8 epochs


-base+reverse+dropout+local-p attention (general) + feed input + unk replace 

![modelimg](https://github.com/sohneunsoo/translator_model/assets/121411251/c5041d10-b3d6-4fe6-802d-6714cf3d23ba)
![imagebleu](https://github.com/sohneunsoo/translator_model/assets/121411251/4898f797-a942-4a0a-9ee3-f1de9392183a)
