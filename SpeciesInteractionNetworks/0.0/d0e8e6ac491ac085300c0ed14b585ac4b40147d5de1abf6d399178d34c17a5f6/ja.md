```
nullmodel(::Type{Connectance}, N::SpeciesInteractionNetwork{<:Partiteness, <:Binary})
```

確率的ネットワークを返します。これは、すべての相互作用がネットワークの接続性に等しい確率で発生するという帰無モデルに基づいています。すなわち、$L$ リンクを持つネットワークで、上部に $|T|$ 種、下部に $|B|$ 種がある場合、

$$
P(i \rightarrow j) = \frac{L}{|T|\times |B|}
$$

[`Unipartite`](@ref) ネットワークの場合、$|T| = |B| = |S|$ です（両側に同じ数の種があります）。

###### 参考文献

[Fortuna2006Habitat](@citet*)
