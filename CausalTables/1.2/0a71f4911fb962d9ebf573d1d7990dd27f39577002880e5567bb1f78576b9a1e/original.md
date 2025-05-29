```
atu(scm::StructuralCausalModel; samples = 10^6)
```

Approximate the average treatment effect among the untreated (ATU) for a given structural causal model (SCM), along with its efficiency bound, for a univariate binary treatment. Mathematically, this is

$$
E(Y(1) - Y(0) \mid A = 0)
$$

where $Y(a)$ represents the counterfactual $Y$ had the treatment $A$ been set to $a$. This statistical quantity is approximated using Monte Carlo sampling.

# Arguments

  * `scm::StructuralCausalModel`: The SCM from which data is to be simulated.
  * `samples`: The number of samples to draw from `scm` for Monte Carlo approximation (default is 10^6). This controls the precision of the approximation.

# Returns

A named tuple containing:

  * `μ`: The ATU approximation.
  * `eff_bound`: The variance of the counterfactual response, which is equal to the efficiency bound for IID data. If observations are correlated, this may not have a meaningful interpretation.

# Example

```@example
using Distributions
dgp = @dgp(
    L ~ Beta(2, 4),
    A ~ @.(Bernoulli(L)),
    Y ~ @.(Normal(A + L))
)
scm = StructuralCausalModel(dgp, :A, :Y, [:L])
atu(scm)
```
