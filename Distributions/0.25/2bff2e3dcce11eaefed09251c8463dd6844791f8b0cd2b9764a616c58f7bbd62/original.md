```
truncated(d0::UnivariateDistribution; [lower::Real], [upper::Real])
truncated(d0::UnivariateDistribution, lower::Real, upper::Real)
```

A *truncated distribution* `d` of a distribution `d0` to the interval $[l, u]=$`[lower, upper]` has the probability density (mass) function:

$$
f(x; d_0, l, u) = \frac{f_{d_0}(x)}{P_{Z \sim d_0}(l \le Z \le u)}, \quad x \in [l, u],
$$

where $f_{d_0}(x)$ is the probability density (mass) function of $d_0$.

The function throws an error if $l > u$.

```julia
truncated(d0; lower=l)           # d0 left-truncated to the interval [l, Inf)
truncated(d0; upper=u)           # d0 right-truncated to the interval (-Inf, u]
truncated(d0; lower=l, upper=u)  # d0 truncated to the interval [l, u]
truncated(d0, l, u)              # d0 truncated to the interval [l, u]
```

The function falls back to constructing a [`Truncated`](@ref) wrapper.

# Implementation

To implement a specialized truncated form for distributions of type `D`, one or more of the following methods should be implemented:

  * `truncated(d0::D, l::T, u::T) where {T <: Real}`: interval-truncated
  * `truncated(d0::D, ::Nothing, u::Real)`: right-truncated
  * `truncated(d0::D, l::Real, u::Nothing)`: left-truncated
