```
mean_field_solution(problem::Problem, β::Vector{<:Real}, γ::Vector{<:Real})
```

### Input

  * `problem::Problem`: A `Problem` instance defining the optimization problem.
  * `β::Vector{<:Real}`: The vector of QAOA driver parameters.
  * `γ::Vector{<:Real}`: The vector of QAOA problem parameters.

### Output

  * The solution bitstring computed for a given problem and schedule parameters.

### Notes

  * This is the first dispatch of `mean_field_solution`, which computes the sought-for solution bitstring for a given problem and schedule parameters.
  * The solution bitstring $\boldsymbol{\sigma}_*$ is defined as follows in terms of the $z$ components of the final spin vectors:

    $\boldsymbol{\sigma}_* = \left(\mathrm{sign}(n_1^z), ..., \mathrm{sign}(n_N^z) \right).$
