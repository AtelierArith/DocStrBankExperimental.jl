```
sample(L::AbstractLEnsemble,k)
```

k-DPPをサンプリングします。すなわち、固定サイズのDPPです。kはLのランクよりも厳密に小さくする必要があります（Lのランクと等しい場合は、ProjectionEnsembleを使用してください）。

このアルゴリズムは、Barthelmé、Amblard、Tremblay（2019）から適応された鞍点近似を使用しています。
