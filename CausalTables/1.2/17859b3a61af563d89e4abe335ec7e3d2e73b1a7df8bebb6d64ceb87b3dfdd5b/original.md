```
cfdiff(scm::StructuralCausalModel, intervention1::Function, intervention2::Function; samples = 10^6)
```

Approximate the difference between two counterfactual response means – that under `intervention1` having been applied to the treatment, and that under `intervention2` – for a given structural causal model (SCM), along with its efficiency bound. Mathematically, this is

$$
E(Y(d_1(a)) - Y(d_2(a)))
$$

where $d_1$ and $d_2$ represent `intervention1` and `intervention2` being applied on the treatment variable(s) $A$. This statistical quantity is approximated using Monte Carlo sampling. 

# Arguments

  * `scm::StructuralCausalModel`: The SCM from which data is to be simulated.
  * `intervention1::Function`: The first intervention function to be contrasted.
  * `intervention2::Function`: The second intervention function to be contrasted.
  * `samples`: The number of samples to draw from `scm` for Monte Carlo approximation (default is 10^6). This controls the precision of the approximation.

# Returns

A named tuple containing:

  * `μ`: The mean difference in counterfactual outcomes.

# Example

```@example
using Distributions
dgp = @dgp(
    L ~ Beta(2, 4),
    A ~ @.(Bernoulli(L)),
    Y ~ @.(Normal(A + L))
)
scm = StructuralCausalModel(dgp, :A, :Y, [:L])
cfdiff(scm, treat_all, treat_none)
```
