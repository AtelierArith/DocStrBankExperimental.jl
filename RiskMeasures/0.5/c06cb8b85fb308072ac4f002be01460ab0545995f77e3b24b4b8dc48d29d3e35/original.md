```
CVaR(x̃, α)
```

Compute the conditional value at risk at level `α` for the random variable `x̃`.

```
CVaR(values, pmf, α; ...)
```

Compute CVaR for a discrete random variable with `values` and the probability mass function `pmf`. 

The risk level `α` must satisfy the $α ∈ [0,1]$. Risk aversion descreses with an increasing `α` and, `α = 1` represents the expectation, `α = 0` computes the essential infimum (smallest value with positive probability).

Assumes a reward maximization setting and solves the dual form

$$
\min_{q ∈ \mathcal{Q}} q^T x̃
$$

where

$$
\mathcal{Q} = \left\{q ∈ Δ^n : q_i ≤ \frac{p_i}{α}\right\}
$$

and $Δ^n$ is the probability simplex, and $p$ is the distribution of $x̃$. 

# Returns

A named tuple with CVaR `value` and the `pmf` that achieves it.

# Keyword Arguments:

  * `check_inputs=true`: check that the inputs are valid.
  * `fast=false`: use linear-time experimental implementation

More details: [https://en.wikipedia.org/wiki/Expected_shortfall](https://en.wikipedia.org/wiki/Expected_shortfall)
