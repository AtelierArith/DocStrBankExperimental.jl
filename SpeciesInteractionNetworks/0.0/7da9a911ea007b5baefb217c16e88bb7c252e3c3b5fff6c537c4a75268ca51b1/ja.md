```
nullmodel(::Type{Generality}, N::SpeciesInteractionNetwork{<:Partiteness, <:Binary})
```

種の脆弱性に比例して相互作用が発生するという帰無モデルの下での確率的ネットワークを返します。すなわち、彼らの期待される入ってくるリンクの数：

$$
P(i \rightarrow j) = \frac{\sum A_{\cdot \rightarrow j}}{|T|}
$$

###### 参考文献

[Poisot2013Facultative](@citet*)

[Weitz2013Phagebacteria](@citet*)
