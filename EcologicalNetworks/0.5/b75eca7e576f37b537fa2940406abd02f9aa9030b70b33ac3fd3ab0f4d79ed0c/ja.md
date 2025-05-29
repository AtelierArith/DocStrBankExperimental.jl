```
linearfilter(N::BinaryNetwork, α::Vector{Float64}=[0.25, 0.25, 0.25, 0.25])
```

ネットワーク `N` に対して、Stock et al. (2017) に従って線形フィルタースコアを計算します。負の相互作用に対する高いスコアは、潜在的な偽陰性または欠落している相互作用を示唆します。これは確率的ネットワークとして返されますが、スコアは必ずしも確率的解釈を伝えるわけではありません。

αの値は、測定された相互作用値、種の外向き次数、種の内向き次数、ネットワークの接続性の順に、*相対的*な重みを与えます。デフォルトのパラメータ設定では、これら4つはすべて同等の重要性を持ちます。

#### 参考文献

Stock, M., Pahikkala, T., Airola, A., Waegeman, W., Baets, B.D., 2018. Algebraic Shortcuts for Leave-One-Out Cross-Validation in Supervised Network Inference. bioRxiv 242321. https://doi.org/10.1101/242321

Stock, M., Poisot, T., Waegeman, W., Baets, B.D., 2017. Linear filtering reveals false negatives in species interaction data. Scientific Reports 7, 45908. https://doi.org/10.1038/srep45908
