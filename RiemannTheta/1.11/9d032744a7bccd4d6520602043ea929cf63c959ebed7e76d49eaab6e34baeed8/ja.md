```
     oscillatory_part(zs::Vector{Vector{ComplexF64}},
                      Ω::Matrix{ComplexF64};
                      eps::Float64=1e-8,
                      derivs::Vector{Vector{ComplexF64}}=Vector{ComplexF64}[],
                      accuracy_radius::Float64=5.)::Vector{ComplexF64}
```

Ωと`zs`のすべてのzに対するリーマンシータ関数の振動部分の値を返します。`derivs`が空である場合、または与えられた方向微分に対する`derivs`のすべてのzに対する導関数を返します。

## パラメータ

  * `zs` : リーマンシータ関数を評価する複素数ベクトルのベクトル。
  * `Omega` : リーマン行列。
  * `eps` : (デフォルト: 1e-8) 希望する数値精度。
  * `derivs` : 方向微分を与える複素数ベクトルのベクトル。
  * `accuracy_radius` : (デフォルト: 5.) 導関数を計算する際にリーマンシータの要求された精度が保証されるg次元原点からの半径。

## 戻り値

  * `z`に現れる各点でのリーマンシータ関数の振動部分の値。
