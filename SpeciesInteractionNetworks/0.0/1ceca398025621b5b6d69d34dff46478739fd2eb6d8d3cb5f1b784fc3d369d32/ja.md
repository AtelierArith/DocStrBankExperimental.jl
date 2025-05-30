```
nullmodel(::Type{Generality}, N::SpeciesInteractionNetwork{<:Partiteness, <:Binary})
```

種の一般性に比例して相互作用が発生するという帰無モデルの下での確率的ネットワークを返します。すなわち、種の期待される外向きリンクの数：

$$
P(i \rightarrow j) = \frac{\sum A_{i \rightarrow \cdot}}{|B|}
$$

###### 参考文献

[Poisot2013Facultative](@citet*)

[Weitz2013Phagebacteria](@citet*)
