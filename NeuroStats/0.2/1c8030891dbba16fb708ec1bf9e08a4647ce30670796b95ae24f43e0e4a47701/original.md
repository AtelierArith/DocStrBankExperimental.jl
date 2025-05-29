```
outlier_detect(x; <keyword arguments>)
```

Detect outliers.

# Arguments

  * `x::AbstractVector`
  * `method::Symbol=iqr`: detecting methods:

      * `:iqr`: interquartile range
      * `:z`: z-score
      * `:g`: Grubbs test

# Returns

  * `o::Vector{Bool}`: index of outliers
