```
y = dur(x::RF)
y = dur(x::Vector{RF})
y = dur(x::Matrix{RF})
```

Duration time in [s] of RF struct or RF Array.

# Arguments

  * `x`: (`::RF` or `::Vector{RF}` or `::Matrix{RF}`) RF struct or RF array

# Returns

  * `y`: (`::Float64`, [`s`]) duration of the RF struct or RF array
