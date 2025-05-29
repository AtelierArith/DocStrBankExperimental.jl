```
flatten(x::AbstractArray)
```

Reshape arbitrarly-shaped input into a matrix-shaped output, preserving the size of the last dimension.

See also [`unsqueeze`](@ref).

# Examples

```jldoctest
julia> rand(3,4,5) |> flatten |> size
(12, 5)
```
