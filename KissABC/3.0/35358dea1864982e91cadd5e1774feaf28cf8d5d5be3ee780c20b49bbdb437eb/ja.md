P. Del Moral 2012による適応SMC、アフィン不変提案メカニズムを使用し、`ABC`ターゲットに対して`AIS`よりも高速です。

```julia
function smc(
    prior::Distribution,
    cost::Function;
    rng::AbstractRNG = Random.GLOBAL_RNG,
    nparticles::Int = 100,
    M::Int = 1,
    alpha = 0.95,
    mcmc_retrys::Int = 0,
    mcmc_tol = 0.015,
    epstol = 0.0,
    r_epstol = (1 - alpha)^1.5 / 50,
    min_r_ess = alpha^2,
    max_stretch = 2.0,
    verbose::Bool = false,
    parallel::Bool = false,
)
```

  * `prior`: パラメータの事前分布を表すDistributionオブジェクト。
  * `cost`: 事前サンプルを与えると、そのサンプルのコストを返す関数（例：シミュレーションデータとターゲットデータの間の距離）。
  * `rng`: SMCが推論に使用するAbstractRNGオブジェクト（推論を再現可能にするのに役立つことがあります）。
  * `nparticles`: 推論に使用する総粒子数。
  * `M`: 粒子ごとのコスト評価の数、これを増やすことで良い粒子を拒否する可能性を減らすことができます。
  * `alpha` - 適応的許容範囲に使用され、`ESS(n,ϵ(n)) = α ESS(n-1, ϵ(n-1))`を`n`ステップで`ϵ(n)`について解く。
  * `mcmc_retrys` - 0より大きく設定された場合、受け入れられた粒子の割合が許容範囲`mcmc_tol`を下回るたびにMCMCステップが繰り返されます（`mcmc_retrys`回を超えない）。
  * `mcmc_tol` - SMCの停止条件、受け入れられた粒子の割合が`mcmc_tol`を下回るとアルゴリズムが終了します。
  * `epstol` - SMCの停止条件、適応コスト閾値が`epstol`を下回るとアルゴリズムが収束し、終了します。
  * `min_r_ess` - 有効サンプルサイズの割合が`min_r_ess`を下回ると、系統的な再サンプリングステップが実行されます。
  * `max_stretch` - `smc`の提案分布はForeman-Mackey et al. 2013のストレッチ移動であり、パラメータが大きくなるほど提案分布が広がります。
  * `verbose` - `true`に設定すると、詳細表示が有効になります。
  * `parallel` - `true`に設定すると、スレッド並列処理が有効になります。この場合、コスト関数はスレッドセーフである必要があります。

# 例

```Julia
using KissABC
prior=Factored(Normal(0,5), Normal(0,5))
cost((x,y)) = 50*(x+randn()*0.01-y^2)^2+(y-1+randn()*0.01)^2
results = smc(prior, cost, alpha=0.5, nparticles=5000).P
```

出力:

```TTY
2-element Array{Particles{Float64,5000},1}:
 1.0 ± 0.029
 0.999 ± 0.012
```
