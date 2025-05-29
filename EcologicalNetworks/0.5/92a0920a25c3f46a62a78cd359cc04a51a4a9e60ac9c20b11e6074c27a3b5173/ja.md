```
linearfilterzoo(N::BinaryNetwork, α::Vector{Float64}=[0.25, 0.25, 0.25, 0.25])
```

ゼロワンアウト版の線形フィルター（`linearfilter`）を計算します。つまり、その相互作用がネットワークで発生しなかった場合の各相互作用のスコアです。例えば、N[4, 6] = 1（種4と6の間の相互作用）の場合、位置(4, 6)の結果は、その相互作用が発生しなかったネットワークを使用したフィルターのスコアです。この関数は、フィルターが偽陰性（欠落）相互作用を検出できるかどうかを検証するのに役立ちます。

#### 参考文献

Stock, M., Pahikkala, T., Airola, A., Waegeman, W., Baets, B.D., 2018. Algebraic Shortcuts for Leave-One-Out Cross-Validation in Supervised Network Inference. bioRxiv 242321. https://doi.org/10.1101/242321

Stock, M., Poisot, T., Waegeman, W., Baets, B.D., 2017. Linear filtering reveals false negatives in species interaction data. Scientific Reports 7, 45908. https://doi.org/10.1038/srep45908
