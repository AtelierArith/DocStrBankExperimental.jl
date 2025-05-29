```
mie_phase_matrix(m, x, μ; norm=:albedo)
```

位相散乱行列を計算します。

単位は $sr^{-1}$ です。位相散乱行列は、K. N. Liou (**2002**) の *An Introduction to Atmospheric Radiation*、第二版の式 5.2.105-6 に従って散乱振幅関数から計算されます。

# パラメータ

  * `m`: 球の複素屈折率
  * `x`: 球のサイズパラメータ
  * `μ`: 位相散乱行列を計算する角度、cos(theta)

# 出力

  * `p`: 位相散乱行列 [$sr^{-1}$]
