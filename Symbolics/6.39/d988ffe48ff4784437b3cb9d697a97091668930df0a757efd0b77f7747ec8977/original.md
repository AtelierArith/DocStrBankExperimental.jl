```
@register_array_symbolic(expr, define_promotion = true)
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

If `define_promotion = true` then a promotion method in the form of

```julia
SymbolicUtils.promote_symtype(::typeof(f_registered), args...) = # inferred or annotated return type
```

is defined for the register function. Note that when defining multiple register overloads for one function, all the rest of the registers must set `define_promotion` to `false` except for the first one, to avoid method overwriting.
