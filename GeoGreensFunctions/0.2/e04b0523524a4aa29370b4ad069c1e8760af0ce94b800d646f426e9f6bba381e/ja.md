```
_stress_vol_tet4(quadrature::Q,
    x1::R, x2::R, x3::R, A::U, B::U, C::U, D::U,
    e11::R, e12::R, e13::R, e22::R, e23::R, e33::R, G::R, nu::R
    ) where {R, U, Q}
```

Tet4要素における非弾性ひずみに起因する応力を計算します。詳細については、特にここで使用されている**座標系**については、[original version](https://bitbucket.org/sbarbot/bssa-2018058/src/default/)を参照してください。

## 引数

  * `quadrature`: 積分のための数値積分法、[FastGaussQuadrature.jl](https://github.com/JuliaApproximation/FastGaussQuadrature.jl)を参照
  * `x1`, `x2`, `x3`: 観測位置
  * `A`, `B`, `C`, `D`: 各頂点の座標を表す3つの数のリスト
  * `e**`: ひずみ成分、各々は$ϵ_{11}$、$ϵ_{12}$、$ϵ_{13}$、$ϵ_{22}$、$ϵ_{23}$、$ϵ_{33}$
  * `G`: せん断弾性係数
  * `nu`: ポアソン比

## 出力

6つの数からなるベクトルで、各々は$σ_{11}$、$σ_{12}$、$σ_{13}$、$σ_{22}$、$σ_{23}$、$σ_{33}$を表します。

## 注意

  * インプレースバージョン: `_stress_vol_tet4!(u, args...)` ここでuは6つの数からなるベクトルです。
