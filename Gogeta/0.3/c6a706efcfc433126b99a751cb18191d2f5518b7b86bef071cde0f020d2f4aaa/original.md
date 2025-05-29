```
function optimize_by_walking!(original::JuMP.Model, nn_model::Flux.Chain, U_in, L_in; delta=0.1, return_sampled=false, silent=true, iterations=10, infeasible_per_iter=5)
```

Performs the full relaxing walk algorithm on the given neural network JuMP formulation. See Tong et al. (2024) for more details.

# Parameters

  * `original`: `JuMP` model containing the NN formulation.
  * `nn_model`: the original NN as `Flux.Chain`

# Optional Parameters

  * `delta`: controls how strongly certain neurons are preferred when fixing the binary variables
  * `return_sampled`: return sampled points in addition to the optima
  * `silent`: print progress info to the console
  * `iterations`: the number of fresh starts from the linear relaxation (no binary variables fixed)
  * `infeasible_per_iter`: the number of infeasible LP relaxations allowed before starting next iteration
