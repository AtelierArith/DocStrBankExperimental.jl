`hyperplane_orbits(W::ComplexReflectionGroup)`

returns  a  list  of  named  tuples,  one  for each hyperplane orbit of the reflection  group `W`. If `o` is the named tuple for such an orbit, and `s` is  the first  element of  `gens(W)` whose  hyperplane is  in the orbit, it contains the following fields

`.s`:     index of `s` in `gens(W)`

`.order`: order of s

`.cl_s`:  for i in `1:order-1`, `position_class(W,W(s)^i)`

`.N_s`:    size of hyperplane orbit

`.det_s`:  for i in `1:order-1`, position in `CharTable(W)` of `detₛⁱ`, where    `detₛ` is the linear character taking the value `det(reflrep(W,s))` on `s`    and `1` on non-conjugate reflections.

```julia-repl
julia> W=coxgroup(:B,2)
B₂

julia> hyperplane_orbits(W)
2-element Vector{@NamedTuple{s::Int64, cl_s::Vector{Int64}, order::Int64, N_s::Int64, det_s::Vector{Int64}}}:
 (s = 1, cl_s = [2], order = 2, N_s = 2, det_s = [5])
 (s = 2, cl_s = [4], order = 2, N_s = 2, det_s = [1])
```
