```
y = dur(x::Grad)
y = dur(x::Vector{Grad})
y = dur(x::Matrix{Grad})
```

Duration time in [s] of Grad struct or Grad Array.

# Arguments

  * `x`: (`::Grad` or `::Vector{Grad}` or `::Matrix{Grad}`) Grad struct or Grad Array

# Returns

  * `y`: (`::Float64`, `[s]`) duration of the Grad struct or Grad Array
