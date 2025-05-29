This type defines the output file for the RAFF algorithm.

```
RAFFOutput(status::Int, solution::Vector{Float64}, iter::Int,
           p::Int, f::Float64, nf::Int, nj::Int, outliers::Vector{Int})
```

where

  * `status`: is 1 if converged and 0 if not
  * `solution`: vector with the parameters of the model
  * `iter`: number of iterations up to convergence
  * `p`: number of trusted points
  * `f`: the residual value
  * `nf`: number of function evaluations
  * `nj`: number of Jacobian evaluations
  * `outliers`: the possible outliers detected by the method, for the given `p`

    RAFFOutput()

Creates a null version of output, equivalent to `RAFFOutput(0, [], -1, 0, Inf, -1, -1, [])`

```
RAFFOuput(p::Int)
RAFFOuput(sol::Vector{Float64}, p::Int)
```

Creates a null version of output for the given `p` and a null version with the given solution, respectively.
