```
haloedge_regions(full_domain::CartesianIndices{N}, axis::Int, nhalo::Int) where {N}
```

`full_domain`のエッジに沿ったハロ領域を幅`nhalo`で抽出し、`full_domain`の内部から対応するエッジ領域を抽出します。これにより、ハロ領域と同じ次元のエッジ領域が作成されます。

# 例

```julia
julia> A = [i for i in 1:10];

julia> full = CartesianIndices(A) # これは全体の "full_domain"
CartesianIndices((10,))

julia> halo, edge = haloedge_regions(full, 1, 2)
(
  halo = (lo = CartesianIndices((1:2,)), hi = CartesianIndices((9:10,))), 
  edge = (lo = CartesianIndices((3:4,)), hi = CartesianIndices((7:8,)))
)
```
