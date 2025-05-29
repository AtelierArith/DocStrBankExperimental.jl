```
TruncatedConjugateGradientState <: AbstractHessianSolverState
```

Steihaug-Tointの切り捨て共役勾配法について説明します。

# フィールド

`T`を接線ベクトルの型、`R <: Real`とします。

  * `δ::T`:                     共役勾配の探索方向
  * `δHδ`, `YPδ`, `δPδ`, `YPδ`: `Hδ`との一時的な内積および前処理された内積。
  * `Hδ`, `HY`:                 `δ`および`Y`に適用されたヘッセ行列の一時的な結果。
  * `κ::R`:                     線形収束の目標率。
  * `project!`:                 数値的安定性のため、各反復後に接線空間に投影することが可能です。この関数は`Y`のインプレースで動作する必要があります。すなわち、`(M, Y, p, X) -> Y`の形で、`X`と`Y`は同じメモリを使用できます。
  * `randomize`:          `X`がランダムベクトルで初期化されるかどうかを示します。
  * `residual::T`:                 モデル$m(Y)$の勾配
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `θ::R`:                     $1+θ$の超線形収束目標率
  * `trust_region_radius::R`:   信頼領域の半径
  * `X::T`:                     勾配$\operatorname{grad}f(p)$
  * `Y::T`:                     現在の反復接線ベクトル
  * `z::T`:                     前処理された残差
  * `z_r::R`:                   残差と`z`の内積

# コンストラクタ

```
TruncatedConjugateGradientState(TpM::TangentSpace, Y=rand(TpM); kwargs...)
```

TCG状態を初期化します。

## 入力

  * `TpM`: [`TangentSpace`](@extref `ManifoldsBase.TangentSpace`)

## キーワード引数

  * `κ=0.1`
  * `project!::F=copyto!`: 数値的安定化を結果をコピーするだけに初期化します。
  * `randomize=false`
  * `θ=1.0`
  * `trust_region_radius=`[`injectivity_radius`](@extref `ManifoldsBase.injectivity_radius-Tuple{AbstractManifold}`)`(base_manifold(TpM)) / 4`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(`[`manifold_dimension`](@extref `ManifoldsBase.manifold_dimension-Tuple{AbstractManifold}`)`(base_manifold(Tpm))``)`[`|`](@ref StopWhenAny)[`StopWhenResidualIsReducedByFactorOrPower`](@ref)`(; κ=κ, θ=θ)`[`|`](@ref StopWhenAny)[`StopWhenTrustRegionIsExceeded`](@ref)`()`[`|`](@ref StopWhenAny)[`StopWhenCurvatureIsNegative`](@ref)`()`[`|`](@ref StopWhenAny)[`StopWhenModelIncreased`](@ref)`()`: 停止基準が満たされていることを示すファンクタ
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 多様体$\mathcal M$の点$p$における接線ベクトル

# 参照

[`truncated_conjugate_gradient_descent`](@ref), [`trust_regions`](@ref) ```
