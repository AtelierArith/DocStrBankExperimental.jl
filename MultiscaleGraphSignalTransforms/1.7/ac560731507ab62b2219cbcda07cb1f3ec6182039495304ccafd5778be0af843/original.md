```
frame_approx(f, U, V; num_kept = length(f))
```

approximate signal `f` by the frame `U`.

# Input Arguments

  * `f::Vector{Float64}`: input graph signal
  * `U::Matrix{Float64}`: a frame operator (matrix or dictionary)
  * `V::Matrix{Float64}`: the dual frame operator of `U`
  * `num_kept::Int64`: number of kept coefficients (NCR)

# Output Argument

  * `rel_error::Vector{Float64}`: the relative errors
  * `f_approx::Vector{Float64}`: the approximated signal
