```
Q(N::T, L::Dict{E,Int64}) where {T<:AbstractEcologicalNetwork,E}
```

ネットワークのモジュラリティとその分割。第二引数は辞書で、`N`のすべての種がモジュールのアイデンティティを表す`Int64`値に関連付けられています。この関数は、二部ネットワークとその単一部投影の同じ値を返します。

#### 参考文献

  * Barber, M.J., 2007. Modularity and community detection in bipartite networks. Phys. Rev. E 76, 066102. https://doi.org/10.1103/PhysRevE.76.066102
  * Newman, M.E., 2006. Modularity and community structure in networks. Proceedings of the national academy of sciences 103, 8577–8582.
