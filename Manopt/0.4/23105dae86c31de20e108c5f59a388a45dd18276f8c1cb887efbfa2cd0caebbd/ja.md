```
PrimalDualSemismoothNewtonState <: AbstractPrimalDualSolverState
```

  * `m`:                         基点 $\mathcal M$ 上の点
  * `n`:                         基点 $\mathcal N$ 上の点
  * `x`:                         初期点 $x^{(0)} ∈ \mathcal M$ （およびその前の反復）
  * `ξ`:                         初期接ベクトル $\xi^{(0)} ∈ T_{n}^*\mathcal N$ （およびその前の反復）
  * `primal_stepsize`:           （`1/sqrt(8)`）プライマルプロキシの近接パラメータ
  * `dual_stepsize`:             （`1/sqrt(8)`）デュアルプロキシの近接パラメータ
  * `reg_param`:                 （`1e-5`）ニュートン行列の正則化パラメータ
  * `stop`:                      a [`StoppingCriterion`](@ref)
  * `update_primal_base`:        （`( amp, ams, i) -> o.m`）プライマルベースを更新する関数
  * `update_dual_base`:          （`(amp, ams, i) -> o.n`）デュアルベースを更新する関数
  * `retraction_method`:         （`default_retraction_method(M, typeof(p))`）使用する再収束法
  * `inverse_retraction_method`: （`default_inverse_retraction_method(M, typeof(p))`）使用する逆再収束法
  * `vector_transport_method`:   （`default_vector_transport_method(M, typeof(p))`）使用するベクトル輸送法

更新関数の引数としては、[`AbstractManoptProblem`](@ref) `amp`、[`AbstractManoptSolverState`](@ref) `ams`、および現在の反復 `i` が必要です。これらをデフォルトの恒等関数とは異なるように設定する場合、アルゴリズムが機能するために `p.Λ` を提供する必要があります（これは `missing` である可能性があります）。

# コンストラクタ

```
PrimalDualSemismoothNewtonState(M::AbstractManifold,
    m::P, n::Q, x::P, ξ::T, primal_stepsize::Float64, dual_stepsize::Float64, reg_param::Float64;
    stopping_criterion::StoppingCriterion = StopAfterIteration(50),
    update_primal_base::Union{Function,Missing} = missing,
    update_dual_base::Union{Function,Missing} = missing,
    retraction_method = default_retraction_method(M, typeof(p)),
    inverse_retraction_method = default_inverse_retraction_method(M, typeof(p)),
    vector_transport_method = default_vector_transport_method(M, typeof(p)),
)
```
