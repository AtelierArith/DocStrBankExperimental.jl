```
kernel_bvp(xs::AbstractArray, ϵ::Number, σ::Number,
           boundary_weights::AbstractVector,
           boundary_values::AbstractVector;
           kernel::Symbol=:SquaredExponential, residuals::Bool=true)
```

不変境界値最小二乗問題を解く

> `min_c ‖GKc‖² + ‖Kc - h_{bd}‖²_bd + ϵ‖c‖²_k = R_inv + R_bd + R_eps`


ここで

  * `‖GKc‖²` は不変性（および可能な非ゼロ平均）を罰するノルム
  * `‖Kc - h_{bd}‖²_bd` は境界条件を違反する関数を罰するノルム
  * `‖c‖²_k` はスムージングカーネルノルム

引数:

  * `xs`: サイズ d × 2N の補間点、ここで xs[:, N+1:2N] = F.(xs[:, 1:N])
  * `ϵ`: 正則化の量
  * `σ`: カーネル幅
  * `boundary_weights`: 長さ `2N` の境界重みベクトル、正であり、|k(x)| << 1 となる点 `x` で O(1) であるべき
  * `boundary_values`: 長さ `2N` の境界値ベクトル、各点で関数が取るべき値を示す
  * `kernel=:SquaredExponential`: 補間するカーネルの種類（`KernelLabel` を参照）
  * `residuals=true`: 問題が残差を返す場合は真。

出力:

  * `k`: カーネル関数

（`residuals=true` の場合）

  * `R`: 総残差
  * `R_bd`: 境界条件残差
  * `R_inv`: 不変性残差
  * `R_eps`: スムーズネス残差

```
