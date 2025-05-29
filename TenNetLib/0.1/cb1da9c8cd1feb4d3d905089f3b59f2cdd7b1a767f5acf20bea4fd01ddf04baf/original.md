```
function position!(sysenv::StateEnvsTTN, node::Int2;
                   maxdim::Int = typemax(Int),
                   mindim::Int = 1,
                   cutoff::Float64 = Float64_threshold(),
                   svd_alg::String = "divide_and_conquer",
                   normalize::Bool = true)
```

Moves the orthogonality center of the TTN to `node` and updates the effective Hamiltonian of the same.

#### Named arguments and their default values:

  * `normalize::Bool = true`: Whether to normalize afterwards.
  * `maxdim::Int = typemax(Int)`: Maximum bond dimension after SVD truncation.
  * `mindim::Int = 1`: Minimum bond dimension after SVD truncation.
  * `cutoff::Float64 = Float64_threshold()`: Cutoff for SVD truncation.
  * `svd_alg::String = "divide_and_conquer"`.
