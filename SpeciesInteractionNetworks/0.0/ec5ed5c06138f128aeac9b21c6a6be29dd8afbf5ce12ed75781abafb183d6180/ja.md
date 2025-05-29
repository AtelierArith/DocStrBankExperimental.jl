```
rdpg(N::SpeciesInteractionNetwork, r::Integer, threshold::T) where {T <: AbstractFloat}
```

ランク `r` のネットワークの [`tsvd`](@ref) に基づいて、ランダムドット積グラフを使用して予測されたバイナリネットワークを返します。スコアが `threshold` を超える相互作用は真であると見なされます。

このRDPGへのアプローチは、強いデータのスパース性の下で非常に予測的であることが示されています [Poisot2023Network](@cite)。

###### 参考文献

[DallaRiva2016Exploring](@citet*)

[Poisot2023Network](@citet*)
