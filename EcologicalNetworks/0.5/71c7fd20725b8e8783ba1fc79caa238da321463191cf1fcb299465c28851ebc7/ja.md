```
information_decomposition(N::AbstractEcologicalNetwork; norm::Bool=false, dims=nothing)
```

与えられた生態ネットワークの情報理論的分解を行います。すなわち、正規化された隣接行列の情報量は以下のように分割されます：

  * `:D` : 一様分布と比較した周辺のエントロピーの差
  * `:I` : 相互情報量
  * `:V` : 情報の変動 / 条件付きエントロピー

`norm=true` の場合、成分はその合計が1になるように正規化されます。オプションで次元を指定することができ、行のインデックスを計算するか（`dims=1`）、列のインデックスを計算するか（`dims=2`）、または全体の行列を計算するか（デフォルト）を示します。

結果はDictで返されます。出力はビット単位です。

Stock, M.; Hoebeke, L.; De Baets, B. « Disentangling the Information in Species Interaction Networks ». Entropy 2021, 23, 703. https://doi.org/10.3390/e23060703
