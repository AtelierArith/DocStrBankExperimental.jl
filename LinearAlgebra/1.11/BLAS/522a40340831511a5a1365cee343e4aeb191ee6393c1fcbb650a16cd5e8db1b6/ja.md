```
axpy!(a, X, Y)
```

スカラー `a` を用いて `Y` を `X*a + Y` で上書きします。`Y` を返します。

# 例

```jldoctest
julia> x = [1.; 2; 3];

julia> y = [4. ;; 5 ;; 6];

julia> BLAS.axpy!(2, x, y)
1×3 Matrix{Float64}:
 6.0  9.0  12.0
```
