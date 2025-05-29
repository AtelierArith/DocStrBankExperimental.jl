```
ConjugateGradientState <: AbstractGradientSolverState
```

共役勾配降下アルゴリズムのオプションを指定します。このアルゴリズムは[`DefaultManoptProblem`]を解決します。

# フィールド

  * `p::P`: 現在の反復を格納する多様体 $\mathcal M$ 上の点
  * `X::T`: 多様体 $\mathcal M$ 上の点 $p$ における接ベクトル
  * `δ`:                       現在の降下方向、接ベクトルでもあります
  * `β`:                       現在の更新係数ルール
  * `coefficient`:             新しい `β` を決定する関数
  * `stepsize::Stepsize`: [`Stepsize`](@ref) から継承されたファンクタで、ステップサイズを決定します
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `retraction_method::AbstractRetractionMethod`: 使用する再traction $\operatorname{retr}$、再tractionに関するセクションを参照してください [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `vector_transport_method::AbstractVectorTransportMethodP`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、ベクトル輸送に関するセクションを参照してください [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

# コンストラクタ

```
ConjugateGradientState(M::AbstractManifold; kwargs...)
```

最後の5つのフィールドはキーワードとして名前で設定でき、`X` はキーワード `initial_gradient` を使用して接ベクトル型に設定でき、デフォルトは `zero_vector(M,p)` であり、`δ` はこのベクトルのコピーで初期化されます。

## キーワード引数

上記のフィールドから以下のキーワード引数を指定できます

  * `initial_gradient=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 多様体 $\mathcal M$ 上の点 $p$ における接ベクトル
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定するための多様体 $\mathcal M$ 上の点
  * `coefficient=[`ConjugateDescentCoefficient`](@ref)`()`: CG係数を指定します。[`ManifoldDefaultsFactory`](@ref) も参照してください。
  * `stepsize=`[`default_stepsize`](@ref)`(M, ConjugateGradientDescentState; retraction_method=retraction_method)`: ステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(500)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-8)`): 停止基準が満たされていることを示すファンクタ
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再traction $\operatorname{retr}$、再tractionに関するセクションを参照してください [the section on retractions](@extref ManifoldsBase :doc:`retractions`)
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、ベクトル輸送に関するセクションを参照してください [the section on vector transports](@extref ManifoldsBase :doc:`vector_transports`)

# 参照

[`conjugate_gradient_descent`](@ref), [`DefaultManoptProblem`](@ref), [`ArmijoLinesearch`](@ref)
