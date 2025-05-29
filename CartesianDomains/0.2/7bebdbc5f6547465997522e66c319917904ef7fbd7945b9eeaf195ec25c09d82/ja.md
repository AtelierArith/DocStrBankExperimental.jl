```
haloedge_regions(full_domain::CartesianIndices{N}, axis::Int, nhalo::Int, nedge::Int) where {N}
```

`full_domain` のエッジに沿ったハロ領域を幅 `nhalo` で抽出し、フルドメインの内部からサイズ `nedge` の対応するエッジ領域を抽出します。これにより、`axis` に沿ったサイズ `nedge` の要素を持つエッジ領域が提供されます。例えば、ハロ領域が2要素のとき、ハロ領域に隣接する最外部のエッジだけを取得したい場合、`haloedge_regions(full_domain, 3, 2, 1)` を呼び出すと、3軸に沿って2要素の厚さのハロ領域が得られますが、エッジ領域は1要素の厚さだけになります。

# 例

```julia
julia> A = [i for i in 1:10];

julia> full = CartesianIndices(A) # これが全体の "full_domain"
CartesianIndices((10,))

julia> halo, edge = haloedge_regions(full, 1, 2, 1) # これはハロ領域2とエッジ1を使用します
(
  halo = (lo = CartesianIndices((1:2,)), hi = CartesianIndices((9:10,))), 
  edge = (lo = CartesianIndices((3:3,)), hi = CartesianIndices((8:8,)))
)
```
