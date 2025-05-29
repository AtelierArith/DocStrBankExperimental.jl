```
function optimize!(sysenv::StateEnvsTTN,
                   params::OptimizeParamsTTN,
                   sweeppath::Vector{Int2};
                   kwargs...)
```

TTNの最適化を実行します。

#### 引数:

  * `sysenv::StateEnvsTTN`.
  * `params::OptimizationParamsTTN`.
  * `sweeppath::Vector{Int2}`: 最適化スイープ中に従うべきパス。すべてのノードを少なくとも一度含む必要があるベクターです。

#### 名前付き引数とそのデフォルト値:

  * `normalize::Bool = true`: 更新後に正規化するかどうか。
  * `svd_alg::String = "divide_and_conquer"`.
  * `weight::Float64 = -1.0`: 励起状態計算のための重み。励起状態最適化のためには`0`より大きく設定する必要があります。
  * `outputlevel::Int = 1`. `0`の場合は情報を出力せず、`1`の場合はフルスイープの後に出力し、`2`の場合は各更新ステップで出力します。

#### 収束基準:

  * `energyErrGoal`: 最適化（特定の段階で）は、2つの連続したスイープ間のエネルギー差がこの閾値を下回ると停止し、最適化は次の段階に移ります。`noise`はこの早期停止をトリガーするために`Float64_threshold()`を下回る必要があります。

#### `eig_solver`のための名前付き引数とそのデフォルト値:

KrylovKit.jlのドキュメントを参照してください。

  * `ishermitian::Bool = true`
  * `solver_tol::Float64 = 1E-14`.
  * `solver_krylovdim::Int = 3`.
  * `solver_maxiter::Int = 1`.
  * `solver_outputlevel::Int = 0`: KrylovKit.jlの`verbosity`を参照してください。
  * `solver_eager::Bool = false`.
  * `solver_check_convergence::Bool = false`.

#### 戻り値:

  * `SweepDataTTN`

```
