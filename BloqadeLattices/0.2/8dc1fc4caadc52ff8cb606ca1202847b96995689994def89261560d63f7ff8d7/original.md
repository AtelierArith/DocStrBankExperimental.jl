```
two_body_interaction_matrix(f, atoms)
```

Generates an interaction matrix given a function `f` that accepts two atom positions at a time  and an indexable iterable `atoms` containing atom positions.

See also [`rydberg_interaction_matrix`](@ref)

```jldoctest; setup=:(using BloqadeLattices)
julia> atoms = [(0.0,), (1.0,), (2.0,), (3.0,)]; # 1D chain, can also be AtomList

julia> two_body_interaction_matrix(atoms) do x,y return 1/distance(x,y) end
4×4 UpperTriangular{Float64, Matrix{Float64}}:
 0.0  1.0  0.5  0.333333
  ⋅   0.0  1.0  0.5
  ⋅    ⋅   0.0  1.0
  ⋅    ⋅    ⋅   0.0
```
