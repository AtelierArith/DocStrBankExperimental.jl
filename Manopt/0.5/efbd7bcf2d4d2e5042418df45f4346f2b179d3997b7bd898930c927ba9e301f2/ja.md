```
StopWhenRelativeResidualLess <: StoppingCriterion
```

相対残差が特定の閾値を下回ったときに停止します。すなわち、

$$
\displaystyle\frac{\lVert r^{(k) \rVert_{}}{c} ≤ ε,
$$

ここで、$c = \lVert b \rVert_{}$ は、$\mathcal A(p)[X] + b(p) = 0_p$ のベクトル場からの初期ベクトルです。[`conjugate_residual`](@ref) から。

# フィールド

  * `at_iteration::Int`: 停止基準が最後に停止を示したイテレーションを示す整数。これは、ソルバーが開始する前（`0`）である可能性もあります。負の値は、まだそのようなことがなかったことを示します；
  * `c`: 初期ノルム
  * `ε`: 閾値
  * `norm_rk`: 残差の最後に計算されたノルム

# コンストラクタ

```
StopWhenRelativeResidualLess(c, ε; norm_r = 2*c*ε)
```

停止基準を初期化します。

!!! note
    内部に保存されているベクトル場の初期ノルム $c = \lVert b \rVert_{}$ は、初期化時に更新されます。つまり、この停止基準が `k<=0` で呼び出された場合です。

