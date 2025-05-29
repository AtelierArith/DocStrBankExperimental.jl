```
ivec(iter)
```

`iter`を反復処理しながらすべての形状を削除します。[`vec`](https://docs.julialang.org/en/stable/base/arrays/#Base.vec)の非物質化バージョンのようなものです。

```jldoctest
julia> m = collect(reshape(1:6, 2, 3))
2×3 Matrix{Int64}:
 1  3  5
 2  4  6

julia> collect(ivec(m))
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```
