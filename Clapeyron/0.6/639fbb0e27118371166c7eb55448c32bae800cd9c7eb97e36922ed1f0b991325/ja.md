```
FugBubblePressure(kwargs...)
```

ファンクション [`bubble_pressure`](@ref) をフガシティ係数を用いて計算します。最初に、相の組成を更新するために逐次代入を使用し、圧力を更新するために外部ニュートンループを使用します。`itmax_newton` 回の反復後に収束が達成されない場合、システムは多次元非線形方程式系を使用して解決されます。

入力:

  * `y0 = nothing`: オプション、蒸気相の組成に対する初期推定
  * `p0 = nothing`: オプション、バブル圧力 [`Pa`] に対する初期推定
  * `vol0 = nothing`: オプション、液相と蒸気相の体積に対する初期推定
  * `itmax_newton = 10`: オプション、ニュートン法を使用して圧力を更新するための反復回数
  * `itmax_ss = 5`: オプション、逐次代入を使用して液相の組成を更新するための反復回数
  * `tol_x = 1e-8`: オプション、逐次代入サイクルを停止するための許容誤差
  * `tol_p = 1e-8`: オプション、ニュートンサイクルを停止するための許容誤差
  * `tol_of = 1e-8`: オプション、目的関数がゼロであるかを確認するための許容誤差
  * `nonvolatiles = nothing`: オプション、揮発性のない化合物を含む文字列のベクター。これらは蒸気相でゼロに設定されます。
