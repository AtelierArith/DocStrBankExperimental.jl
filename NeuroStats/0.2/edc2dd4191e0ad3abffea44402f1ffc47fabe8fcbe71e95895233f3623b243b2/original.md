```
msci95(s; <keyword arguments>)
```

Calculate mean, standard deviation and 95% confidence interval.

# Arguments

  * `s::AbstractMatrix`
  * `n::Int64=3`: number of bootstraps
  * `method::Symbol=:normal`: use normal method (`:normal`) or `n`-times boostrapping (`:boot`)

# Returns

Named tuple containing:

  * `sm::Vector{Float64}`: mean
  * `ss::Vector{Float64}`: standard deviation
  * `su::Vector{Float64}`: upper 95% CI
  * `sl::Vector{Float64}`: lower 95% CI
