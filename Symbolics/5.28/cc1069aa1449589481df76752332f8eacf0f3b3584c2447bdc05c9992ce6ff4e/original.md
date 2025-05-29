```
@register_array_symbolic(expr)
```

Example:

```julia
# Let's say vandermonde takes an n-vector and returns an n x n matrix
@register_array_symbolic vandermonde(x::AbstractVector) begin
    size=(length(x), length(x))
    eltype=eltype(x) # optional, will default to the promoted eltypes of x
end
```

You can also register calls on callable structs:

```julia
@register_array_symbolic (c::Conv)(x::AbstractMatrix) begin
    size=size(x) .- size(c.kernel) .+ 1
    eltype=promote_type(eltype(x), eltype(c))
end
```
