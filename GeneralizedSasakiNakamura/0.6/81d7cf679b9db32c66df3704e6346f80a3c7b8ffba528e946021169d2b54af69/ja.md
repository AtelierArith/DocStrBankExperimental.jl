```
GSN_radial(s::Int, l::Int, m::Int, a, omega, boundary_condition, rsin, rsout; horizon_expansion_order::Int=_DEFAULT_horizon_expansion_order, infinity_expansion_order::Int=_DEFAULT_infinity_expansion_order, method="auto", data_type=Solutions._DEFAULTDATATYPE,  ODE_algorithm=Solutions._DEFAULTSOLVER, tolerance=Solutions._DEFAULTTOLERANCE, rsmp=nothing)
```

与えられたモード（`s` スピン重み、`l` ハーモニックインデックス、`m` 方位インデックス、`a` ケルスピンパラメータ、`omega` 周波数 [*複素数であることができる*] で指定）および `boundary_condition` で指定された境界条件に対して GSN 関数を計算します。境界条件は次のいずれかです。

```
- `IN` は地平線での純粋な入射、
- `UP` は無限大での純粋な出射、
- `OUT` は地平線での純粋な出射、
- `DOWN` は無限大での純粋な入射。
```

`OUT` および `DOWN` の解は、それぞれ `IN` および `UP` の解を線形結合することによって構築されます。

GSN 関数は、実数の `omega` に対して、*トルテーズ座標* $r_{*} \in$ `[rsin, rsout]` の範囲で ODE ソルバー（`DifferentialEquations.jl` から）を使用して数値的に解かれます。これは `ODE_algorithm` によって指定され（デフォルト: `Vern9()`）、`tolerance` によって指定された許容誤差（デフォルト: `1e-12`）で解かれます。解くべき ODE は、キーワード `method`（デフォルト: `auto`）によって決定され、`linear`（GSN 方程式を線形形式で解く）または `Riccati`（GSN 方程式を非線形形式で解く）のいずれかです。デフォルトで使用されるデータ型は `ComplexF64`（すなわち倍精度浮動小数点数）ですが、`data_type` を指定することで変更できます（例: 複素数の任意精度数のための `Complex{BigFloat}`）。

複素数の `omega` に対して、GSN 関数は $r_*$ の複素平面上の回転した経路に沿って解かれます。この経路は、実数変数/新しい座標 $\rho$ でパラメータ化された 2 つの折れ線セグメントから構成されます。経路が回転する角度は、周波数 $\omega$、ケルスピンパラメータ $a$、および方位インデックス $m$ によって決定され、GSN 関数は地平線および空間的無限大近くで平面波のように振る舞います。$\rho = 0$ のとき、経路は $r_{*} = r_{*}^{\rm{mp}}$（`rsmp`、デフォルトは何も指定しない、つまり自動的に決定される）で実軸と交差します。数値的および半解析的 GSN 解は、現在複素数の $r_{*}$ の代わりに $\rho$ の関数として評価されます。

数値的 GSN 解は `[rsin, rsout]` の範囲内でのみ正確ですが、完全な GSN 解は、地平線近く（`horizon_expansion_order`-次まで）および無限大近く（`infinity_expansion_order`-次まで）の漸近解を滑らかに接続することによって構築されます。したがって、現在の半解析的 GSN 解は *どこでも正確* です。

ただし、`omega = 0` の場合、ガウスの超幾何関数を使用して表現された正確な GSN 関数が返されます（すなわち、数値的に解かれるのではなく）。この場合、`s`、`l`、`m`、`a`、`omega`、`boundary_condition` のみが解析されます。

GSN 解に関するすべての情報を含む `GSNRadialFunction` オブジェクトを返します。
