```
varimax(A; gamma = 1.0, minit = 20, maxit = 1000, reltol = 1e-12)
```

VARIMAX perform varimax (or quartimax, equamax, parsimax) rotation to the column vectors of the input matrix.

# Input Arguments

  * `A::Matrix{Float64}`: input matrix, whose column vectors are to be rotated. d, m = size(A).
  * `gamma::Float64`: default is 1. gamma = 0, 1, m/2, and d(m - 1)/(d + m - 2), corresponding to quartimax, varimax, equamax, and parsimax.
  * `minit::Int`: default is 20. Minimum number of iterations, in case of the stopping criteria fails initially.
  * `maxit::Int`: default is 1000. Maximum number of iterations.
  * `reltol::Float64`: default is 1e-12. Relative tolerance for stopping criteria.

# Output Argument

  * `B::Matrix{Float64}`: output matrix, whose columns are already been rotated.

Implemented by Haotian Li, Aug. 20, 2019
