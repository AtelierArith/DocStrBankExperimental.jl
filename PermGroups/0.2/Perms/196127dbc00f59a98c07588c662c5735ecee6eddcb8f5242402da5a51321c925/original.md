`orbits(a::Perm,d::AbstractVector{<:Integer};trivial=true)`

returns  the orbits of `a` on domain `d`, which should be a union of orbits of `a`. If `trivial=false`, does not return the orbits of length `1`.

# Example

```julia-repl
julia> orbits(Perm(1,2)*Perm(4,5),1:5)
3-element Vector{Vector{Int64}}:
 [1, 2]
 [3]
 [4, 5]
```
