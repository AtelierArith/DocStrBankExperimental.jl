```
findnan(y::AbstractVector; maxgap::Int=Inf)
```

Find the indices of `NaN` values in the vector `y`, but only if the run of `NaN`s is less than or equal to `maxgap`.

# Arguments

  * `y::AbstractVector`: The input vector to search for `NaN` values.
  * `maxgap::Int=Inf`: The maximum allowed length of consecutive `NaN` values to be included in the result. Runs of `NaN`s longer than this will be ignored.

# Returns

  * `Vector{Int}`: A vector of indices where `NaN` values are found, considering the `maxgap` constraint.

# Example

```julia
y = [1.0, NaN, NaN, 4.0, NaN, NaN, NaN, 8.0]
findnan(y, maxgap=2) # returns [2, 3]
findnan(y, maxgap=3) # returns [2, 3, 5, 6, 7]
```
