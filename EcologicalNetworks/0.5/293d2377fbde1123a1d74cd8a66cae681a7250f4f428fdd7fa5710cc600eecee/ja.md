```
each_species_its_module(N::T) where {T<:AbstractEcologicalNetwork}
```

各種がそれぞれ自分自身のモジュールである辞書を返します。これは内部的に `lp` と `salp` の出発点として使用されます。これはしばしば `brim` にとって非常に悪い出発点であり、単独で使用すべきではないでしょう。

#### 参考文献

Thébault, E., 2013. Identifying compartments in presence–absence matrices and bipartite networks: insights into modularity measures. Journal of Biogeography 40, 759–768. https://doi.org/10.1111/jbi.12015
