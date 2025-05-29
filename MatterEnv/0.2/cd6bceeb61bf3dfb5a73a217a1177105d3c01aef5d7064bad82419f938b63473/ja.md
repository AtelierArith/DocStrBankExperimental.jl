```
projection_transformation!(projection::ProjectionWithSpin,
    transfer_matrix::Matrix{<:Number}...;
    orbit::Symbol=:d)
```

射影の線形変換 ⟨Yₗₘ|ϕₙₖ⟩。

# 引数

  * `projection::ProjectionWithSpin`: 波動関数の射影
  * `transfer_matrix::Matrix{<:Number}...`: 変換行列 M1, M2 ...
  * `orbit::Symbol=:d`: 変換で考慮される軌道、デフォルトは d 軌道
