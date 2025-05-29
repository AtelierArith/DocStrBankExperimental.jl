```
NodeFunctionRuleFallback(extractfn = mean)
```

指定された関数（デフォルト：mean）を使用して、メッセージと周辺分布を値に変換する`Stochastic`ノードのフォールバックルールです。これは、メッセージを作成するために`nodefunction`メソッドを呼び出します。

ノードが`@node`マクロで定義されるとき：

1. `nodefunction`は通常、ノードの分布に関連付けられた`logpdf`を呼び出します。 2. `@node`仕様の最初のエッジは、`logpdf`を評価するために使用されます。 3. 他のエッジは、関連する分布オブジェクトをインスタンス化するために使用されます。

```julia
julia> using ReactiveMP, BayesBase, Distributions

julia> struct MyBeta{A, B} <: ContinuousUnivariateDistribution
             a::A
             b::B
       end

julia> BayesBase.logpdf(d::MyBeta, x) = logpdf(Beta(d.a, d.b), x)

julia> BayesBase.insupport(d::MyBeta, x::Real) = true

julia> @node MyBeta Stochastic [out, a, b]

julia> message = @call_rule [fallback = NodeFunctionRuleFallback()] MyBeta(:out, Marginalisation) (m_a = Beta(2, 3), m_b = Beta(3, 2));

julia> logpdf(message, 0.5)
-0.5017644952110732

julia> message = @call_rule [fallback = NodeFunctionRuleFallback(mode)] MyBeta(:out, Marginalisation) (m_a = Beta(2, 3), m_b = Beta(3, 2)); # evaluate at `mode`

julia> logpdf(message, 0.5)
-0.5954237415153454
```
