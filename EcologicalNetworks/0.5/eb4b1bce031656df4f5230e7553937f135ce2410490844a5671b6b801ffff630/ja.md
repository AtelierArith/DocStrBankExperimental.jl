```
omnivory(N::T) where {T <: UnipartiteNetwork}
```

豊富さ richness(N) の長さを持つ消費のインデックスをトロフィックレベルにわたって返します。食事の寄与は、獲物種の次数に比例して均等に分散されると明示的に仮定します。オムニボリーは `trophic_level` の出力に基づいて測定されます。

#### 参考文献

  * Christensen, Villy, and Daniel Pauly. "ECOPATH II—a software for balancing steady-state ecosystem models and calculating network characteristics." Ecological modelling 61, no. 3-4 (1992): 169-185.
