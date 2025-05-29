```
shuffleobs([rng], data)
```

Return a version of the dataset `data` that contains all the origin observations in a random reordering.

The values of `data` itself are not copied. Instead only the indices are shuffled. This function calls [`obsview`](@ref) to accomplish that, which means that the return value is likely of a different type than `data`.

Optionally, a random number generator `rng` can be passed as the first argument. 

For this function to work, the type of `data` must implement [`numobs`](@ref) and [`getobs`](@ref). 

See also [`obsview`](@ref).

# Examples

```julia
# For Arrays the subset will be of type SubArray
@assert typeof(shuffleobs(rand(4,10))) <: SubArray

# Iterate through all observations in random order
for x in eachobs(shuffleobs(X))
    ...
end
```
