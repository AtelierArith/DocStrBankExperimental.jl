```
@rule NodeType(:Edge, Constraint) (Arguments..., [ meta::MetaType ]) = begin
    # rule body
    return ...
end
```

The `@rule` macro help to define new methods for the `rule` function. It works particularly well in combination with the `@node` macro. It has a specific structure, which must specify:

  * `NodeType`: must be a valid Julia type. If some attempt to define a rule for a Julia function (for example `+`), use `typeof(+)`
  * `Edge`: edge label, usually edge labels are defined with the `@node` macro
  * `Constrain`: DEPRECATED, please just use the `Marginalisation` label
  * `Arguments`: defines a list of the input arguments for the rule

      * `m_*` prefix indicates that the argument is of type `Message` from the edge `*`
      * `q_*` prefix indicates that the argument is of type `Marginal` on the edge `*`
  * `Meta::MetaType` - optionally, a user can specify a `Meta` object of type `MetaType`.  This can be useful is some attempts to try different rules with different approximation methods or if the rule itself requires some temporary storage or cache.  The default meta is `nothing`.

Here are various examples of the `@rule` macro usage:

1. Belief-Propagation (or Sum-Product) message update rule for the `NormalMeanVariance` node  toward the `:μ` edge with the `Marginalisation` constraint. Input arguments are `m_out` and `m_v`, which are the messages from the corresponding edges `out` and `v` and have the type `PointMass`.

```julia
@rule NormalMeanVariance(:μ, Marginalisation) (m_out::PointMass, m_v::PointMass) = NormalMeanVariance(mean(m_out), mean(m_v))
```

2. Mean-field message update rule for the `NormalMeanVariance` node towards the `:μ` edge with the `Marginalisation` constraint. Input arguments are `q_out` and `q_v`, which are the marginals on the corresponding edges `out` and `v` of type `Any`.

```julia
@rule NormalMeanVariance(:μ, Marginalisation) (q_out::Any, q_v::Any) = NormalMeanVariance(mean(q_out), mean(q_v))
```

3. Structured Variational message update rule for the `NormalMeanVariance` node towards the `:out` edge with the `Marginalisation` constraint. Input arguments are `m_μ`, which is a message from the `μ` edge of type `UnivariateNormalDistributionsFamily`, and `q_v`, which is a marginal on the `v` edge of type `Any`.

```julia
@rule NormalMeanVariance(:out, Marginalisation) (m_μ::UnivariateNormalDistributionsFamily, q_v::Any) = begin
    m_μ_mean, m_μ_cov = mean_cov(m_μ)
    return NormalMeanVariance(m_μ_mean, m_μ_cov + mean(q_v))
end
```

See also: [`rule`](@ref), [`marginalrule`](@ref), [`@marginalrule`], [`@call_rule`](@ref)
