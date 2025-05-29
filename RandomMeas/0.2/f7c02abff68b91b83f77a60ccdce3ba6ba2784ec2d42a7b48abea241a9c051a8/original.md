```
trace(shadows::AbstractArray{<:AbstractShadow})
```

Compute the trace for each shadow in a collection of shadow objects.

# Arguments:

  * `shadows::AbstractArray{<:AbstractShadow}`: A collection (vector, matrix, etc.) of shadow objects.

# Returns

An array of scalar trace values corresponding to each shadow, with the same dimensions as the input.
