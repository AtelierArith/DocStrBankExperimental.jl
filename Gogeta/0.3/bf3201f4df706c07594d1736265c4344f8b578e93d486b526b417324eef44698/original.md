```
function local_search(start, jump_model, U_in, L_in; max_iter=100, epsilon=0.01, show_path=false, silent=true, tolerance=0.001)
```

Performs relaxing walk local search on the given neural network JuMP formulation. See Tong et al. (2024) for more details.

# Parameters

  * `start`: starting point for the search (coordinate in the space)
  * `jump_model`: `JuMP` model containing the NN formulation
  * `U_in`: upper bounds for the domain
  * `L_in`: lower bounds for the domain

# Optional Parameters

  * `epsilon`: controls the step size taken out of the linear region
  * `show_path`: return the path taken by the local search in addition to the optimum
  * `silent`: print progress info to console
  * `tolerance`: minimum relative improvement required at every step to continue the search
