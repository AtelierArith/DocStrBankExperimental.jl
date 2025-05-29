```
axpby!(a, X, b, Y)
```

スカラー `a` と `b` を用いて `Y` を `X*a + Y*b` で上書きします。`Y` を返します。

# 例

```jldoctest
julia> x = [1., 2, 3];

julia> y = [4., 5, 6];

julia> BLAS.axpby!(2., x, 3., y)
3-element Vector{Float64}:
 14.0
 19.0
 24.0
```
