```
mdiff(s1, s2; <keyword arguments>)
```

Calculate mean difference and 95% confidence interval for 2 signals.

# Arguments

  * `s1::AbstractMatrix`
  * `s2::AbstractMatrix`
  * `n::Int64=3`: number of bootstraps
  * `method::Symbol=:absdiff`:

      * `:absdiff`: maximum difference
      * `:diff2int`: integrated area of the squared difference

# Returns

Named tuple containing:

  * `st::Vector{Float64}`
  * `sts::Float64`
  * `p::Float64`
