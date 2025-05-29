```
msci95(s; <keyword arguments>)
```

Calculate mean, standard deviation and 95% confidence interval.

# Arguments

  * `s::AbstractVector`
  * `n::Int64=3`: number of bootstraps
  * `method::Symbol=:normal`: use normal method (`:normal`) or `n`-times boostrapping (`:boot`)

# Returns

Named tuple containing:

  * `sm::Float64`: mean
  * `ss::Float64`: standard deviation
  * `su::Float64`: upper 95% CI
  * `sl::Float64`: lower 95% CI
