```
links_variance(N::SpeciesInteractionNetwork{<:Partiteness, <:Probabilistic})
```

確率的ネットワークにおけるリンクの期待数の分散は、$p \times (1 - p)$の合計として定義されます。ここで、$p$はすべての相互作用の確率（$p = 0$を含む）です。

###### 参考文献

[Poisot2015structure](@citet*)
