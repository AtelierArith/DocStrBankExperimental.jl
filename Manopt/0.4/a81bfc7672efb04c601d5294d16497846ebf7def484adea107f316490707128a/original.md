```
PolyakStepsize <: Stepsize
```

Compute a step size

$$
α_i = \frac{f(p^{(i)}) - f_{\text{best}}+γ_i}{\lVert{ ∂f(p^{(i)})} \rVert^2},
$$

where $f_{\text{best}}$ is the best cost value seen until the current iteration, and $γ_i$ is a sequence of numbers that is square summable, but not summable (the sum must diverge to infinity). Furthermore $∂f$ denotes a subgradient of $f$ at the current iterate $p^{(i)}$.

The step size is an adaption from the Dynamic step size discussed in Section 3.2 of [Bertsekas:2015](@cite), both to the Riemannian case and to approximate the minimum cost value.

# Fields

  * `γ`               : a function `i -> ...` representing the sequence.
  * `best_cost_value` : storing the value `f_{\text{best}}`

# Constructor

```
PolyakStepsize(;
    γ = i -> 1/i,
    initial_cost_estimate=0.0
)
```

initialize the Polyak stepsize to a certain sequence and an initial estimate of $f_{\text{best}}$
