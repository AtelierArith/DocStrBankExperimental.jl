```
histogram(array; bins=minimum([100, length(array)]), normalization=:uniform, custom_range=false)
```

# Description

```
Compute the histogram of an array. Useful for barplot in GLMakie.
```

# Arguments

  * `array::AbstractArray`: Array to compute the histogram of.

# Keyword Arguments

  * `bins::Integer`: Number of bins to use.
  * `normalization::AbstractArray`: Normalization to use. If `:uniform`, then the normalization is uniform.
  * `custom_range::Tuple`: Custom range to use. If `false`, then the range is computed from the data.

# Returns

  * `Tuple{AbstractArray, AbstractArray}`: Tuple of the bin centers and the histogram values.
