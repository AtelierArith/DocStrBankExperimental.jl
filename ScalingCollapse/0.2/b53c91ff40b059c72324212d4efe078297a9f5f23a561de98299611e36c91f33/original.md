```
scaled_data(sp::ScalingProblem)
scaled_data(sp::ScalingProblem, ps)
```

Return the scaled data of the `ScalingProblem` `sp`.

# Arguments

  * `sp::ScalingProblem`: scaling problem
  * `ps::Vector{Float64}=sp.optimal_ps`: parameters to scale the data with (manually)

# Returns

  * `xs::Vector{Vector{Float64}}`: scaled x values
  * `ys::Vector{Vector{Float64}}`: scaled y values
  * `es::Vector{Vector{Float64}}`: scaled y error values
  * `Ls::Vector{Float64}`: scaled system sizes
