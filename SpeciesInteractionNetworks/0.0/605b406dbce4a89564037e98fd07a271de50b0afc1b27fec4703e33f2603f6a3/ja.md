```
nullmodel(::Type{Degree}, N::SpeciesInteractionNetwork{<:Partiteness, <:Binary})
```

すべての相互作用が、関与する種が確立しているリンクの数に比例して、一般性と脆弱性の平均と等しい確率で発生するという帰無モデルの下での確率的ネットワークを返します：

$$
P(i \rightarrow j) = \frac{1}{2}\left(\frac{\sum A_{i \rightarrow \cdot}}{|B|} + \frac{\sum A_{\cdot \rightarrow j}}{|T|} \right)
$$

###### 参考文献

[Bascompte2003nested](@citet*)
