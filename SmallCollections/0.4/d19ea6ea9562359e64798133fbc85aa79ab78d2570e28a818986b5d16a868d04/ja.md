```
sum_fast(v::AbstractSmallVector{N,T}) where {N,T}
```

`v`の要素の`@fastmath`合計を返します。`sum`とは異なり、戻り値は常に`v`の要素型になります。これは小さなビット整数の場合でも同様です。

`Base.sum`、`Base.@fastmath`も参照してください。

# 例

```jldoctest
julia> v = SmallVector{4}([-0.0, -0.0])
2-element SmallVector{4, Float64}:
 -0.0
 -0.0

julia> sum(v), sum_fast(v)
(-0.0, 0.0)

julia> v = SmallVector{4}(Int8[80, 90])
2-element SmallVector{4, Int8}:
 80
 90

julia> sum(v), sum_fast(v)
(170, -86)
```
