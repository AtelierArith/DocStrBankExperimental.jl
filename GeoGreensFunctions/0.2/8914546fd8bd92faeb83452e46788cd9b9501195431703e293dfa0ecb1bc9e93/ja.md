```
_disp_vol_tet4(quadrature::Q,
    x1::R, x2::R, x3::R, A::U, B::U, C::U, D::U,
    e11::R, e12::R, e13::R, e22::R, e23::R, e33::R, nu::R
    ) where {R, U, Q}
```

Tet4要素における非弾性ひずみに起因する変位を計算します。詳細については、特にここで使用されている**座標系**については[original version](https://bitbucket.org/sbarbot/bssa-2018058/src/default/)を参照してください。

## 引数

  * `quadrature`: 積分のための数値積分ルール、[FastGaussQuadrature.jl](https://github.com/JuliaApproximation/FastGaussQuadrature.jl)を参照
  * `x1`, `x2`, `x3`: 観測位置、$x_{3} ≥ 0$であること
  * `A`, `B`, `C`, `D`: 各頂点の座標を表す3つの数のリスト。すべての深さ座標は0以上でなければなりません（ここではチェックは行われません）
  * `e**`: ひずみ成分、各々は$ϵ_{11}$、$ϵ_{12}$、$ϵ_{13}$、$ϵ_{22}$、$ϵ_{23}$、$ϵ_{33}$
  * `nu`: ポアソン比

## 出力

3つの数のベクトル、各々は$u_{1}$、$u_{2}$、$u_{3}$を表します。

## 注意

  * インプレースバージョン: `_disp_vol_tet4!(u, args...)` ここでuは3つの数のベクトルです。
