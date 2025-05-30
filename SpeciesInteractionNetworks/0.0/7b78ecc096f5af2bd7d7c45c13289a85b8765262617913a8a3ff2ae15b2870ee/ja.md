```
rdpg(N::SpeciesInteractionNetwork, r::Integer)
```

ランク `r` のネットワークの [`tsvd`](@ref) を用いたランダムドット積グラフを使用して予測された定量的ネットワークを返します。

RDPGは、転移学習の文脈においても食物網の構造を予測することが示されています [Strydom2022Food](@cite)。

###### 参考文献

[DallaRiva2016Exploring](@citet*)

[Strydom2022Food](@citet*)
