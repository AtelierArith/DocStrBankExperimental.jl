```
parent{T<:AbstractPath}(fp::T) -> T
```

Returns the parent of the supplied path. If no parent exists then either "/" or "." will be returned depending on whether the path is absolute.

# Example

```jldoctest
julia> parent(p"~/.julia/v0.6/REQUIRE")
p"~/.julia/v0.6"

julia> parent(p"/etc")
p"/"

julia> parent(p"etc")
p"."

julia> parent(p".")
p"."
```
