```
function dmrg!(sysenv::StateEnvs, params::DMRGParams, nsite::Int; kwargs...)
```

DMRGを実行します。

#### 引数:

  * `sysenv::StateEnvs`。
  * `params::DMRGParams`。
  * 環境の`nsite::Int`。1サイト更新の場合は`1`、2サイト更新の場合は`2`。

#### 名前付き引数とそのデフォルト値:

  * `normalize::Bool = true`: 更新後に正規化するかどうか。
  * `svd_alg::String = "divide_and_conquer"`。
  * `weight::Float64 = -1.0`: 励起状態DMRGのための重み。励起状態DMRGのためには`0`より大きく設定する必要があります。
  * `outputlevel::Int = 1`。`0`の場合は情報を出力せず、`1`の場合はフルスイープごとに出力し、`2`の場合は各更新ステップで出力します。

#### 収束基準:

  * `energyErrGoal`: DMRG（特定の段階で）は、2回の連続スイープ間のエネルギー差がこの閾値を下回ると停止し、次の段階に進みます。`noise`はこの早期停止をトリガーするために`Float64_threshold()`を下回る必要があります。
  * `entropyErrGoal`: DMRG（特定の段階で）は、2回の連続スイープ間の中間チェーンエントロピー差がこの閾値を下回ると停止し、次の段階に進みます。`noise`はこの早期停止をトリガーするために`Float64_threshold()`を下回る必要があります。

`energyErrGoal`と`entropyErrGoal`の両方が与えられた場合、両方の条件を満たす必要があります。

#### `solver`のための名前付き引数とそのデフォルト値:

KrylovKit.jlのドキュメントを参照してください。

  * `ishermitian::Bool = true`。
  * `solver_tol::Float64 = 1E-14`。
  * `solver_krylovdim::Int = 5`。
  * `solver_maxiter::Int = 2`。
  * `solver_outputlevel::Int = 0`。KrylovKit.jlの`verbosity`を参照してください。
  * `solver_eager::Bool = false`。
  * `solver_check_convergence::Bool = false`。

#### 戻り値:

  * `SweepData`

```
