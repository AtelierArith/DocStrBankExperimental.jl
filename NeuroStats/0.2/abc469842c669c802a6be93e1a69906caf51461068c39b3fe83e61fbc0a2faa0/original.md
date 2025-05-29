```
count_thresh(x; <keyword arguments>)
```

Collect thresholded elements, e.g. in a topographical map.

# Arguments

  * `x::AbstractMatrix`
  * `t::Real`: threshold value
  * `t_type::Symbol=:g`: rule for thresholding:

      * `:eq`: =
      * `:geq`: ≥
      * `:leq`: ≤
      * `:g`: >
      * `:l`: <

# Returns

Named tuple containing:

  * `x_t::Matrix{Bool}`: thresholded matrix
  * `n::Int64`: number of elements
