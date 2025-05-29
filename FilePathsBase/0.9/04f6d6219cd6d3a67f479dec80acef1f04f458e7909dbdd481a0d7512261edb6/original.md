```
parents{T<:AbstractPath}(fp::T) -> Array{T}
```

Return all parents of the path. If no parent exists then either "/" or "." will be returned depending on whether the path is absolute.

# Example

```jldoctest
julia> parents(p"~/.julia/v0.6/REQUIRE")
3-element Array{PosixPath,1}:
 p"~"
 p"~/.julia"
 p"~/.julia/v0.6"

julia> parents(p"/etc")
1-element Array{PosixPath,1}:
 p"/"

julia> parents(p"etc")
1-element Array{PosixPath,1}:
 p"."

julia> parents(p".")
1-element Array{PosixPath,1}:
 p"."
```
