```
cfmean(scm::StructuralCausalModel, intervention::Function; samples = 10^6)
```

Approximate the counterfactual mean of the response had `intervention` been applied to the treatment, along with its efficiency bound, for a given structural causal model (SCM). Mathematically, this estimand is

$$
E(Y(d(a)))
$$

where $d(a)$ represents an intervention on the treatment variable(s) $A$. This statistical quantity is approximated using Monte Carlo sampling. 

# Arguments

  * `scm::StructuralCausalModel`: The SCM from which data is to be simulated.
  * `intervention::Function`: The intervention function to apply to the SCM.
  * `samples`: The number of samples to draw from `scm` for Monte Carlo approximation (default is 10^6). This controls the precision of the approximation.

# Returns

A named tuple containing:

  * `μ`: The mean of the counterfactual outcomes.

# Example

```@example
using Distributions
dgp = @dgp(
    L ~ Beta(2, 4),
    A ~ @.(Bernoulli(L)),
    Y ~ @.(Normal(A + L))
)
scm = StructuralCausalModel(dgp, :A, :Y, [:L])
cfmean(scm, treat_all)
cfmean(scm, treat_none)
```
