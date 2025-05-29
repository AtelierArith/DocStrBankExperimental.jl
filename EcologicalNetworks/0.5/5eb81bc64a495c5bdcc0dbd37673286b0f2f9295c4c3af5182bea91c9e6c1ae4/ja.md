```
brim(N::NT, L::Dict{E,Int64}) where {NT<:AbstractEcologicalNetwork,E}
```

BRIMを使用して生態ネットワークのモジュラリティを最適化します。`L`引数は、ネットワーク内のすべての種をそのモジュールにマッピングする辞書です。この関数は、ネットワークとそのモジュール割り当てのタプルを返します。

#### 参考文献

  * Barber, M.J., 2007. Modularity and community detection in bipartite networks. Phys. Rev. E 76, 066102. https://doi.org/10.1103/PhysRevE.76.066102
  * Newman, M.E., 2006. Modularity and community structure in networks. Proceedings of the national academy of sciences 103, 8577–8582.
  * Thébault, E., 2013. Identifying compartments in presence–absence matrices and bipartite networks: insights into modularity measures. Journal of Biogeography 40, 759–768. https://doi.org/10.1111/jbi.12015
