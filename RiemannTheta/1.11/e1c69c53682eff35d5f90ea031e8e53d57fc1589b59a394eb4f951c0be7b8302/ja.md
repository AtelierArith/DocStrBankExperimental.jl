```
 riemanntheta(zs::Vector{Vector{ComplexF64}},
```

                  Ω::Matrix{ComplexF64};                   eps::Float64=1e-8,                   derivs::Vector{Vector{ComplexF64}}=Vector{ComplexF64}[],                   accuracy_radius::Float64=5.)::Vector{ComplexF64}

Ωに対するリーマンシータ関数の値を返し、`zs`内のすべてのzに対して、`derivs`が空である場合、または与えられた方向微分に対して`derivs`内のすべてのzの微分を返します。

## パラメータ

  * `zs` : リーマンシータ関数を評価する複素ベクトルのベクトル。
  * `Omega` : リーマン行列。
  * `eps` : (デフォルト: 1e-8) 希望する数値精度。
  * `derivs` : 方向微分を与える複素ベクトルのベクトル。
  * `accuracy_radius` : (デフォルト: 5.) 微分を計算する際にリーマンシータの要求された精度が保証されるg次元原点からの半径。シータの微分が要求されていない場合は使用されません。

## 戻り値

`zs`内の各点におけるリーマンシータ関数の値（または微分）。
