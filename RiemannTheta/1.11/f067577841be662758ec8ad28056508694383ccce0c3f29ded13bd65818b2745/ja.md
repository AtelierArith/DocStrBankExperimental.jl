```
     exponential_part(zs::Vector{Vector{ComplexF64}},
                      Ω::Matrix{ComplexF64})::Vector{Float64}
```

Ωと`zs`のすべてのzに対するリーマンシータ関数の指数部分の値を返します。

## パラメータ

  * `zs` : リーマンシータ関数を評価する複素ベクトルのベクトル。
  * `Omega` : リーマン行列。

## 戻り値

`zs`に現れる各点でのリーマンシータ関数の指数部分の値。
