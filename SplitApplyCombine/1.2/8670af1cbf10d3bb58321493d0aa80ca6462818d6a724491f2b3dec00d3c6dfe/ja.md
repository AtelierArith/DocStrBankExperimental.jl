```
productview(f, a, b)
```

`a` と `b` の直積のビューを返し、出力要素は `a` と `b` のそれぞれに対して評価された `f` です。`product` と `ProductArray` も参照してください。

# 例

```julia
julia> productview(+, [1,2], [1,2,3])
2×3 ProductArray{Int64,2,typeof(+),Array{Int64,1},Array{Int64,1}}:
 2  3  4
 3  4  5
```
