`cycletype(a::Perm,domain::AbstractVector{<:Integer};trivial=true)`

`domain`  should be  a union  of orbits  of `a`.  Returns the  partition of `length(domain)`  associated to the conjugacy class of `a` in the symmetric group  of `domain`, with ones removed if `trivial=false` (in which case the partition does not depend on `domain` but just on `support(a)`)

`cycletype(a::Perm)`

returns `cycletype(a,1:last_moved(a);trivial=false)`

# Example

```julia-repl
julia> cycletype(Perm(1,2)*Perm(4,5))
2-element Vector{Int64}:
 2
 2

julia> cycletype(Perm(1,2)*Perm(4,5),1:5)
3-element Vector{Int64}:
 2
 2
 1

julia> cycletype(Perm(1,2)*Perm(4,5),1:6)
4-element Vector{Int64}:
 2
 2
 1
 1
```
