```
msci95(s; <keyword arguments>)
```

Calculate mean, standard deviation and 95% confidence interval.

# Arguments

  * `s::AbstractArray`
  * `n::Int64=3`: number of bootstraps
  * `method::Symbol=:normal`: use normal method (`:normal`) or `n`-times boostrapping (`:boot`)

# Returns

Named tuple containing:

  * `sm::Matrix{Float64}`: mean
  * `ss::Matrix{Float64}`: standard deviation
  * `su::Matrix{Float64}`: upper 95% CI
  * `sl::Matrix{Float64}`: lower 95% CI
