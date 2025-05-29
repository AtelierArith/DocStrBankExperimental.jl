```
boundaryExtension(β::AbstractArray{T,1},
                  k::Int,
                  ::Type{BOUNDARY_EXT_TYPE})
```

境界拡張タイプ `BOUNDARY_EXT_TYPE` に基づいて、拡張境界値 `β[k]` を計算します。

利用可能な `BOUNDARY_EXT_TYPE` は次のとおりです：

  * `ZeroPaddingBE`: ゼロパディング
  * `ConstantBE`: 定数境界拡張パディング
  * `PeriodicBE`: 周期的境界拡張パディング
  * `MirrorBE`: ミラー対称境界拡張パディング

このルーチンは、`k` 値に制限がないという点で堅牢です。

```jldoctest
julia> dom = [-5:10;];

julia> hcat(dom,map(x->boundaryExtension([1; 2; 3],x,ZeroPaddingBE),dom))'
2×16 adjoint(::Matrix{Int64}) with eltype Int64:
 -5  -4  -3  -2  -1  0  1  2  3  4  5  6  7  8  9  10
  0   0   0   0   0  0  1  2  3  0  0  0  0  0  0   0

julia> hcat(dom,map(x->boundaryExtension([1; 2; 3],x,ConstantBE),dom))'
2×16 adjoint(::Matrix{Int64}) with eltype Int64:
 -5  -4  -3  -2  -1  0  1  2  3  4  5  6  7  8  9  10
  1   1   1   1   1  1  1  2  3  3  3  3  3  3  3   3

julia> hcat(dom,map(x->boundaryExtension([1; 2; 3],x,PeriodicBE),dom))'
2×16 adjoint(::Matrix{Int64}) with eltype Int64:
 -5  -4  -3  -2  -1  0  1  2  3  4  5  6  7  8  9  10
  1   2   3   1   2  3  1  2  3  1  2  3  1  2  3   1

julia> hcat(dom,map(x->boundaryExtension([1; 2; 3],x,MirrorBE),dom))'
2×16 adjoint(::Matrix{Int64}) with eltype Int64:
 -5  -4  -3  -2  -1  0  1  2  3  4  5  6  7  8  9  10
  3   2   1   2   3  2  1  2  3  2  1  2  3  2  1   2

```
