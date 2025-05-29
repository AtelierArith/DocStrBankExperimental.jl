```
unname(::Name{name}) where name
```

Inverse of [`Name`](@ref).

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> @inferred unname(Name(:a))
:a
```
