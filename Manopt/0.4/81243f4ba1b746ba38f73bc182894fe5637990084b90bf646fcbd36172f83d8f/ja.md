```
StopWhenRelativeResidualLess <: StoppingCriterion
```

相対残差が特定の閾値を下回ったときに停止します。すなわち、

$$
  \frac{\lVert r^{(k)} \rVert}{c} ≤ ε,
$$

ここで $c = \lVert b \rVert$ は、ベクトル場の初期ベクトルからのもので、$\mathcal A(p)[X] + b(p) = 0_p$ の式における [`conjugate_residual`](@ref) からのものです。

# フィールド

  * `at_iteration` は、停止基準が満たされたイテレーション（`i=0` を含む）を示し、満たされていない間は `-1` です。
  * `c`: 初期ノルム
  * `ε`: 閾値
  * `norm_rk`: 残差の最後に計算されたノルム

# コンストラクタ

```
StopWhenRelativeResidualLess(c, ε; norm_r = 2*c*ε)
```

停止基準を初期化します。

!!! note
    内部に保存されているベクトル場の初期ノルム $c = \lVert b \rVert$ は、初期化時に更新されます。つまり、この停止基準が `k<=0` で呼び出された場合です。

