```
ape(scm::StructuralCausalModel, intervention::Function; samples = 10^6)
```

Approximate the average policy effect for a given structural causal model (SCM), along with its efficiency bound. This is also known as the causal effect of a modified treatment policy, and is approximated using Monte Carlo sampling. Note that unless `intervention` is piecewise smooth invertible, the estimated statistical quantity may not have a causal interpretation; see [Haneuse and Rotnizky (2013)](https://pubmed.ncbi.nlm.nih.gov/23913589/). Mathematically, this is

$$
E(Y(d(a) - Y(a))
$$

where $d(a)$ represents the intervention on the treatment variable(s) $A$, $Y(d(a))$ represents the counterfactual $Y$ under treatment $d(a)$, and $Y(a)$ represents the counterfactual outcome under the naturally observed value of treatment. This statistical quantity is approximated using Monte Carlo sampling.

Convenience functions for generating `intervention` functions include `additive_mtp` and `multiplicative_mtp`, which construct functions that respectively add or multiply a constant (or constant vector) to the treatment variable(s). One can also implement their own intervention function; this function must take as input a `CausalTable` object and return a NamedTuple object with each key indexing a treatment variable that has been modified according to the intervention. Also see `cast_matrix_to_table_function` for a convenience function for constructing interventions.

# Arguments

  * `scm::StructuralCausalModel`: The SCM from which data is to be simulated.
  * `intervention::Function`: The intervention function to apply to the SCM.
  * `samples`: The number of samples to draw from `scm` for Monte Carlo approximation (default is 10^6). This controls the precision of the approximation.

# Returns

A named tuple containing:

  * `μ`: The ATU approximation.

# Example

```@example
using Distributions
dgp = CausalTables.@dgp(
    L ~ Beta(2, 4),
    A ~ @.(Normal(L)),
    Y ~ @.(Normal(A + 2 * L + 1))
)
scm = CausalTables.StructuralCausalModel(dgp, [:A], [:Y], [:L])
ape(scm, additive_mtp(0.5))
ape(scm, multiplicative_mtp(2.0))

# example of a custom intervention function
custom_intervention = cast_matrix_to_table_function(x -> exp.(x))
ape(scm, custom_intervention)

```
