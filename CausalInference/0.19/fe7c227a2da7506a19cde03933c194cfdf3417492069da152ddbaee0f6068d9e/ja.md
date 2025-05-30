```
kl_renyi(data::Array{Float64, 2}, q; k=5)
```

データのRenyi-alphaエントロピーの最近傍推定を計算します。

dataは2次元配列で、各列が1つのデータポイントを表します。詳細については、次を参照してください。

"A class of Rényi information estimators for multidimensional densities" Nikolai Leonenko, Luc Pronzato, and Vippal Savani The Annals of Statistics, 2008 https://projecteuclid.org/euclid.aos/1223908088

キーワード引数: k=5: 最近傍の数
