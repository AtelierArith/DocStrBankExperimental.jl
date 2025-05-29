```
ConjugateResidualState{T,R,TStop<:StoppingCriterion} <: AbstractManoptSolverState
```

[`conjugate_residual`](@ref) ソルバーの状態です。

# フィールド

  * `X::T`: イテレート
  * `r::T`: 残差 $r = -b(p) - \mathcal A(p)[X]$
  * `d::T`: 共役方向
  * `Ar::T`, `Ad::T`: $\mathcal A(p)[d]$, $\mathcal A(p)[r]$ のストレージ
  * `rAr::R`: $⟨ r, \mathcal A(p)[r] ⟩$ を格納する内部フィールド
  * `α::R`: ステップ長
  * `β::R`: 共役係数
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ

# コンストラクタ

```
ConjugateResidualState(TpM::TangentSpace,slso::SymmetricLinearSystemObjective; kwargs...)
```

デフォルト値で状態を初期化します。

## キーワード引数

  * `r=-`[`get_gradient`](@ref)`(TpM, slso, X)`
  * `d=copy(TpM, r)`
  * `Ar=`[`get_hessian`](@ref)`(TpM, slso, X, r)`
  * `Ad=copy(TpM, Ar)`
  * `α::R=0.0`
  * `β::R=0.0`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(`[`manifold_dimension`](@extref `ManifoldsBase.manifold_dimension-Tuple{AbstractManifold}`)`(M)``)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-8)`: 停止基準が満たされていることを示すファンクタ
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 多様体 $\mathcal M$ の点 $p$ における接ベクトル

# 参照

[`conjugate_residual`](@ref)
