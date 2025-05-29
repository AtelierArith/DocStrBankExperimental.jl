```
NodeFunctionRuleFallback(extractfn = mean)
```

A fallback rule for `Stochastic` nodes that uses a specified function (default: mean) to transform messages and marginals into a value.  It calls the `nodefunction` method to create the message.

When a node is defined with the `@node` macro:

1.	The `nodefunction` typically calls `logpdf` associated with the node's distribution. 2.	The first edge in the `@node` specification is used to evaluate `logpdf` at. 3.	Other edges are used to instantiate the associated distribution object.

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
