```
ConjugateResidualState{T,R,TStop<:StoppingCriterion} <: AbstractManoptSolverState
```

[`conjugate_residual`](@ref) ソルバーの状態。

# フィールド

  * `X::T`: イテレート
  * `r::T`: 残差 $r = -b(p) - \mathcal A(p)[X]$
  * `d::T`: 共役方向
  * `Ar::T`, `Ad::T`: $\mathcal A$ のストレージ
  * `rAr::R`: $⟨ r, \mathcal A(p)[r] ⟩$ を格納する内部フィールド
  * `α::R`: ステップ長
  * `β::R`: 共役係数
  * `stop::TStop`: ソルバーのための [`StoppingCriterion`](@ref)

# コンストラクタ

```
    function ConjugateResidualState(
        TpM::TangentSpace,
        slso::SymmetricLinearSystemObjective;
        X=rand(TpM),
        r=-get_gradient(TpM, slso, X),
        d=copy(TpM, r),
        Ar=get_hessian(TpM, slso, X, r),
        Ad=copy(TpM, Ar),
        α::R=0.0,
        β::R=0.0,
        stopping_criterion=StopAfterIteration(manifold_dimension(TpM)) |
                           StopWhenGradientNormLess(1e-8),
        kwargs...,
)

デフォルト値で状態を初期化します。
```
