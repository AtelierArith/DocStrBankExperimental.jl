```
@marginalrule NodeType(:Cluster) (Arguments..., [ meta::MetaType ]) = begin
    # rule body
    return ...
end
```

The `@marginalrule` macro help to define new methods for the `marginalrule` function. It works particularly well in combination with the `@node` macro. It has a specific structure, which must specify:

  * `NodeType`: must be a valid Julia type. If some attempt to define a rule for a Julia function (for example `+`), use `typeof(+)`
  * `Cluster`: edge cluster that contains joined edge labels with the `_` symbol. Usually edge labels are defined with the `@node` macro
  * `Arguments`: defines a list of the input arguments for the rule

      * `m_*` prefix indicates that the argument is of type `Message` from the edge `*`
      * `q_*` prefix indicates that the argument is of type `Marginal` on the edge `*`
  * `Meta::MetaType` - optionally, a user can specify a `Meta` object of type `MetaType`.  This can be useful is some attempts to try different rules with different approximation methods or if the rule itself requires some temporary storage or cache.  The default meta is `nothing`.

The `@marginalrule` can return a `NamedTuple` in the `return` statement. This would indicate some variables in the joint marginal  for the `Cluster` are independent and the joint itself is factorised. For example if some attempts to compute a marginal for the `q(x, y)` it is possible to return `(x = ..., y = ...)` as the result of the computation to indicate that `q(x, y) = q(x)q(y)`.

Here are various examples of the `@marginalrule` macro usage:

1. Marginal computation rule around the `NormalMeanPrecision` node for the `q(out, μ)`. The rule accepts arguments `m_out` and `m_μ`, which are the messages

from the `out` and `μ` edges respectively, and `q_τ` which is the marginal on the edge `τ`.

```julia
@marginalrule NormalMeanPrecision(:out_μ) (m_out::UnivariateNormalDistributionsFamily, m_μ::UnivariateNormalDistributionsFamily, q_τ::Any) = begin
    xi_out, W_out = weightedmean_precision(m_out)
    xi_μ, W_μ     = weightedmean_precision(m_μ)

    W_bar = mean(q_τ)

    W  = [W_out+W_bar -W_bar; -W_bar W_μ+W_bar]
    xi = [xi_out; xi_μ]

    return MvNormalWeightedMeanPrecision(xi, W)
end
```

2. Marginal computation rule around the `NormalMeanPrecision` node for the `q(out, μ)`. The rule accepts arguments `m_out` and `m_μ`, which are the messages from the

`out` and `μ` edges respectively, and `q_τ` which is the marginal on the edge `τ`. In this example the result of the computation is a `NamedTuple`

```julia
@marginalrule NormalMeanPrecision(:out_μ) (m_out::PointMass, m_μ::UnivariateNormalDistributionsFamily, q_τ::Any) = begin
    return (out = m_out, μ = prod(ClosedProd(), NormalMeanPrecision(mean(m_out), mean(q_τ)), m_μ))
end
```
