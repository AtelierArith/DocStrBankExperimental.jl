```
AdaptiveRegularizationState{P,T} <: AbstractHessianSolverState
```

[`adaptive_regularization_with_cubics`](@ref) ソルバーの状態。

# フィールド

初期化時にパラメータを省略できる場合は、デフォルト値が括弧内に示されています。

  * `η1`, `η2`:           （`0.1`, `0.9`）正則化パラメータを評価するための境界
  * `γ1`, `γ2`:           （`0.1`, `2.0`）正則化パラメータ `σ` の縮小および拡大係数
  * `p`:                  （`rand(M)` 現在の反復点
  * `X`:                  （`zero_vector(M,p)`）現在の勾配 $\operatorname{grad}f(p)$
  * `s`:                  （`zero_vector(M,p)`）接空間 $\mathcal T_{p} \mathcal M$ でモデル問題を最小化した結果の接ベクトルステップ
  * `σ`:                  現在の立方体正則化パラメータ
  * `σmin`:               （`1e-7`）立方体正則化パラメータの下限
  * `ρ_regularization`:   （`1e3`）ρを計算するための正則化パラメータ。

収束に近づくと、分子と分母がゼロに近づくため、ρを計算するのが難しくなることがあります。比を正則化することで、ρは収束近くで1に近づきます。

  * `evaluation`:         （`AllocatingEvaluation()`）提供する場合
  * `retraction_method`:  （`default_retraction_method(M)`）使用する再収縮
  * `stopping_criterion`: （[`StopAfterIteration`](@ref)`(100)`) [`StoppingCriterion`](@ref)
  * `sub_problem`:        各反復で解決されるサブ問題
  * `sub_state`:          サブソルバーのための [`AbstractManoptSolverState`](@ref)

さらに、以下の積分フィールドが定義されています。

  * `q`:                  （`copy(M,p)`）モデルとρを評価するための候補点
  * `H`:                  （`copy(M, p, X)`）現在のヘッセ行列、$\operatorname{Hess}F(p)[⋅]$
  * `S`:                  （`copy(M, p, X)`）サブソルバーからの現在の解
  * `ρ`:                  実際の改善とモデル改善の現在の正則化比。
  * `ρ_denominator`:      （`one(ρ)`）警告またはエラーを許可するためにρの計算から分母を格納する値。この値が非正のとき。

# コンストラクタ

```
AdaptiveRegularizationState(M, p=rand(M); X=zero_vector(M, p); kwargs...)
```

すべてのフィールドをキーワード引数として指定してソルバー状態を構築します。
