```
censored(d0::UnivariateDistribution; [lower::Real], [upper::Real])
censored(d0::UnivariateDistribution, lower::Real, upper::Real)
```

A *censored distribution* `d` of a distribution `d0` to the interval $[l, u]=$`[lower, upper]` has the probability density (mass) function:

$$
f(x; d_0, l, u) = \begin{cases}
    P_{Z \sim d_0}(Z \le l), & x = l \\
    f_{d_0}(x),              & l < x < u \\
    P_{Z \sim d_0}(Z \ge u), & x = u \\
  \end{cases}, \quad x \in [l, u]
$$

where $f_{d_0}(x)$ is the probability density (mass) function of $d_0$.

If $Z \sim d_0$, and `X = clamp(Z, l, u)`, then $X \sim d$. Note that this implies that even if $d_0$ is continuous, its censored form assigns positive probability to the bounds $l$ and $u$. Therefore, a censored continuous distribution has atoms and is a mixture of discrete and continuous components.

The function falls back to constructing a [`Distributions.Censored`](@ref) wrapper.

# Usage

```julia
censored(d0; lower=l)           # d0 left-censored to the interval [l, Inf)
censored(d0; upper=u)           # d0 right-censored to the interval (-Inf, u]
censored(d0; lower=l, upper=u)  # d0 interval-censored to the interval [l, u]
censored(d0, l, u)              # d0 interval-censored to the interval [l, u]
```

# Implementation

To implement a specialized censored form for distributions of type `D`, instead of overloading a method with one of the above signatures, one or more of the following methods should be implemented:

  * `censored(d0::D, l::T, u::T) where {T <: Real}`
  * `censored(d0::D, ::Nothing, u::Real)`
  * `censored(d0::D, l::Real, ::Nothing)`
