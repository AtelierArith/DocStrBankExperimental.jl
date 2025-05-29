```
stochastic_gradient_descent(M, grad_f, p=rand(M); kwargs...)
stochastic_gradient_descent(M, msgo; kwargs...)
stochastic_gradient_descent!(M, grad_f, p; kwargs...)
stochastic_gradient_descent!(M, msgo, p; kwargs...)
```

確率的勾配降下法を実行します。これは `p` のインプレースで実行できます。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `grad_f`: 勾配関数で、勾配のベクトルを返すか、勾配関数のベクトルである必要があります
  * `p`: 多様体 $\mathcal M$ 上の点

勾配の代わりに [`ManifoldStochasticGradientObjective`](@ref) `msgo` を提供することもでき、その場合、`cost=` キーワードは効果がありません。なぜなら、その場合、コストはすでに目的の中に含まれているからです。

# キーワード引数

  * `cost=missing`: 例えば関数値を追跡するためのコスト関数を提供できます
  * `direction=`[`StochasticGradient`](@ref)`([`zero*vector`](@extref`ManifoldsBase.zero*vector-Tuple{AbstractManifold, Any}`)`(M, p)`)
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることによって動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であるため、修正された引数は2番目になります。
  * `evaluation_order=:Random`: ランダムに順序を入れ替えたシーケンスを使用するか（`:FixedRandom`）、サイクルごとに順序を入れ替えたシーケンス（`:Linear`）またはデフォルトの `:Random` を使用するかを指定します。
  * `order_type=:RandomOder`: 勾配評価の順序のタイプ。可能な値は `:RandomOrder`、`:FixedPermutation`、`:LinearOrder` です。
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(1000)`: 停止基準が満たされていることを示すファンクタ
  * `stepsize=`[`default_stepsize`](@ref)`(M, StochasticGradientDescentState)`: ステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `order=[1:n]`: 初期の順列で、`n` は `gradF` の勾配の数です。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再収束 $\operatorname{retr}$、再収束に関するセクションを参照してください [the section on retractions](@extref ManifoldsBase :doc:`retractions`)

他のすべてのキーワード引数は、状態デコレーターのために [`decorate_state!`](@ref) に、目的デコレーターのために [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの最終状態全体を取得するには、詳細については [`get_solver_return`](@ref) を参照してください。特に `return_state=` キーワードに注意してください。
