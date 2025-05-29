```
_stress_vol_hex8(
    x1::R, x2::R, x3::R, q1::R, q2::R, q3::R,
    L::R, T::R, W::R, theta::R,
    epsv11p::R, epsv12p::R, epsv13p::R, epsv22p::R, epsv23p::R, epsv33p::R,
    G::R, nu::R,
    ) where R
```

Hex8要素における非弾性ひずみに起因する応力を計算します。     詳細については[原版](https://bitbucket.org/sbarbot/bssa-2016237/src/master/)を参照してください。特にここで使用される**座標系**に注意してください。

## 引数

[`_disp_vol_hex8`](@ref)と同じです。

## 出力

6つの数値のベクトルで、各々は$σ_{11}$、$σ_{12}$、$σ_{13}$、     $σ_{22}$、$σ_{23}$、$σ_{33}$を表します。

## 注意

  * インプレースバージョン: `_stress_vol_hex8!(u, args...)` ここでuは6つの数値のベクトルです。
