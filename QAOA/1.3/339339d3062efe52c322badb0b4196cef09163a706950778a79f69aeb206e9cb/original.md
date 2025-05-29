```
anneal(problem::Problem, beta::Vector{Float64}, gamma::Vector{Float64})
```

An extra function to do quantum annealing for a given problem instead of the QAOA.

### Input

  * `problem::Problem`: A `Problem` instance defining the optimization problem.
  * `beta::Vector{Float64}`: A vector of schedule parameters multiplying the transverse-field or driver Hamiltonian.
  * `gamma::Vector{Float64}`: A vector of schedule parameters multiplying the problem or computational-basis Hamiltonian.

### Output

  * `probabilities::Vector{Float64}`: The vector of output probabilities over the bitstrings.

### Notes

A good choice for the parameters `beta` and `gamma` is given in Appendix A of https://arxiv.org/abs/1907.02359. ``
