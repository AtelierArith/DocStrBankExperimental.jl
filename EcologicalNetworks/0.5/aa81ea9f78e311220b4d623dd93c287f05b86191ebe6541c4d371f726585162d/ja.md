```
find_motif(N::T1, m::T2) where {T1<:AbstractEcologicalNetwork, T2<:BinaryNetwork}
```

モチーフの一部である種を含むタプルの配列を返します。配列の長さは、モチーフが見つかった回数を示します。確率的ネットワークの場合、タプルにはモチーフの正しい構成で種を観察する確率と分散も含まれます。

#### 参考文献

  * Milo, R., Shen-Orr, S., Itzkovitz, S., Kashtan, N., Chklovskii, D., Alon, U.,

    2002. ネットワークモチーフ：複雑なネットワークの単純な構成要素。Science 298,

    824–7. https://doi.org/10.1126/science.298.5594.824
  * Poisot, T., Cirtwill, A.R., Cazelles, K., Gravel, D., Fortin, M.-J., Stouffer, D.B., 2016. 確率的ネットワークの構造。Methods in Ecology and Evolution 7, 303–312. https://doi.org/10.1111/2041-210X.12468
