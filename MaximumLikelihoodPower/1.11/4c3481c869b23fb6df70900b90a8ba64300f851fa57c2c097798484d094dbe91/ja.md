```
mleKS{T<:AbstractFloat}(data::AbstractVector{T})
```

ソートされたベクトル `data` に適用されたべき法則の指数の最大尤度推定値と標準誤差を返します。また、コルモゴロフ-スミルノフ統計量も返します。結果は `MLEKS` 型のインスタンスで返されます。
