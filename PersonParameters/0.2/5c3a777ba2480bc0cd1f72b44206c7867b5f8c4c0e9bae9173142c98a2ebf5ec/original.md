```julia
se(pp)

```

Extract the standard error from a [`PersonParameter`](@ref) estimate `pp`.

## Examples

```jldoctest
julia> pp = PersonParameter(0.5, 0.3);

julia> se(pp)
0.3
```
