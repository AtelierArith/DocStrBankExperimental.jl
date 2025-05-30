```
kaiser_denormalize(Λ, weights)
```

正規化されたローディング行列 `Λ` のカイザー正規化を与えられた `weights` に基づいて元に戻します。

## 例

```jldoctest
julia> L = [
           0.830 -0.396
           0.818 -0.469
           0.777 -0.470
           0.798 -0.401
           0.786  0.500
           0.672  0.458
           0.594  0.444
           0.647  0.333
       ];

julia> L_norm, weights = kaiser_normalize(L);

julia> L_denorm = kaiser_denormalize(L_norm, weights)
8×2 Matrix{Float64}:
 0.83   -0.396
 0.818  -0.469
 0.777  -0.47
 0.798  -0.401
 0.786   0.5
 0.672   0.458
 0.594   0.444
 0.647   0.333

julia> L ≈ L_denorm
true

```
