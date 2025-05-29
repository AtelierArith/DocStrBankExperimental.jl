```
mean_squared_error(results::AbstractVector{Tuple{<:Number,<:Number}})
```

Returns the mean squared error of `results`.

# Arguments

  * `results<:AbstractVector{<:Tuple{Number,Number}}`: the vector of tuples, where each tuple is in the form `Tuple{expected_output, actual_output}`.
