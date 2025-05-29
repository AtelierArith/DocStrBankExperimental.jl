```
rydberg_interaction_matrix(atoms, C::Real)
rydberg_interaction_matrix(lattice::BoundedLattice{L,R},C::Real)
```

Generate the interaction matrix given an indexable iterable `atoms` containg atom positions and the Rydberg interaction constant `C`.

A `BoundedLattice` can be used in place of `atoms` which generates the Rydberg interaction matrix for the lattice, factoring in Periodic Boundary Conditions.

See also [`two_body_interaction_matrix`](@ref)

```jldoctest; setup=:(using BloqadeLattices)
julia> atoms = [(0.0,), (1.0,), (2.0,), (3.0,)]; # 1D chain of atoms

julia> rydberg_interaction_matrix(atoms, 2π * 862690) # provide Rydberg constant
4×4 UpperTriangular{Float64, Matrix{Float64}}:
 0.0  5.42044e6  84694.4         7435.45
  ⋅   0.0            5.42044e6  84694.4
  ⋅    ⋅             0.0            5.42044e6
  ⋅    ⋅              ⋅             0.0

julia> bl = parallelepiped_region(SquareLattice(),(2,0),(0,2);pbc=true); 

julia> rydberg_interaction_matrix(bl, 2π * 862690)
4×4 UpperTriangular{Float64, Matrix{Float64}}:
 0.0  5.42044e6  5.42044e6  6.77555e5
  ⋅   0.0        6.77555e5  5.42044e6
  ⋅    ⋅         0.0        5.42044e6
  ⋅    ⋅          ⋅         0.0
```
