```
Teukolsky_radial(s::Int, l::Int, m::Int, a, omega, boundary_condition, rsin, rsout; horizon_expansion_order::Int=_DEFAULT_horizon_expansion_order, infinity_expansion_order::Int=_DEFAULT_infinity_expansion_order, method="auto", data_type=Solutions._DEFAULTDATATYPE,  ODE_algorithm=Solutions._DEFAULTSOLVER, tolerance=Solutions._DEFAULTTOLERANCE, rsmp=nothing)
```

指定されたモード（`s`はスピン重み、`l`は調和数、`m`は方位数、`a`はカーのスピンパラメータ、`omega`は周波数[これは*複素数*である可能性があります]）と、`boundary_condition`によって指定された境界条件に対してテュコルスキー関数を計算します。境界条件は次のいずれかです。

```
- `IN`はホライズンでの純粋な入射、
- `UP`は無限大での純粋な出射、
- `OUT`はホライズンでの純粋な出射、
- `DOWN`は無限大での純粋な入射。
```

`OUT`および`DOWN`の解は、それぞれ`IN`および`UP`の解を線形結合することによって構築されることに注意してください。

完全なGSN解は対応するテュコルスキー解$(R(r), dR/dr)$に変換され、入射、反射および透過振幅はGSN形式からテュコルスキー形式に変換され、透過振幅は1に正規化されるという正規化規約（すなわち`normalization_convention=UNIT_TEUKOLSKY_TRANS`）が適用されます。

ただし、`omega = 0`の場合、ガウスの超幾何関数を使用して表現された正確なテュコルスキー関数が返されます（すなわち、GSN形式を使用する代わりに）。この場合、`s`、`l`、`m`、`a`、`omega`、`boundary_condition`のみが解析されます。

複素数の`omega`の値に対して、テュコルスキー関数は$r$の関数として評価され、複素平面上の回転した積分経路に沿った対応する位置$\rho = r_{*}(r) \in \mathbb{R}$での値が返されます。
