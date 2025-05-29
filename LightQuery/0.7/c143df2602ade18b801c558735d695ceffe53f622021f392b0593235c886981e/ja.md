```
unname(::Name{name}) where name
```

[`Name`](@ref) の逆。

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> @inferred unname(Name(:a))
:a
```
