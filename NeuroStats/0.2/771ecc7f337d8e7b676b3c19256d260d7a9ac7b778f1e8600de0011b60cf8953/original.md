```
mdiff(s1, s2; <keyword arguments>)
```

Calculate mean difference and its 95% CI between channels.

# Arguments

  * `s1::AbstractArray`
  * `s2::AbstractArray`
  * `n::Int64=3`: number of bootstraps
  * `method::Symbol=:absdiff`

      * `:absdiff`: maximum difference
      * `:diff2int`: integrated area of the squared difference

# Returns

Named tuple containing:

  * `st::Matrix{Float64}`
  * `sts::Vector{Float64}`
  * `p::Vector{Float64}`
