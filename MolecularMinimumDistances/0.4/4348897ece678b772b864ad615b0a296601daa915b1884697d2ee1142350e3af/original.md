```
SelfPairs(;
    xpositions::AbstractVector{<:AbstractVector{T}},
    cutoff::T,
    unitcell::AbstractVecOrMat,
    xn_atoms_per_molecule::Int,
    parallel::Bool=true
) where T<:Real
```

Initializes a particle system for the calculation of minimum distances within a single set of molecules. The shortest distance of each molecule to any other molecule of the same set is computed.

Instead of the number of atoms per molecule, the user can also provide a  more general `mol_indices` function, which, for each atomic index, returns the  corresponding molecular index (which is `mol_indices(i) = (i-1)%n + 1` where `n` is the number of atoms per molecule if all molecules have the same number of atoms and are continously stored in the array of positions). 

# Examples

```julia-repl
julia> using MolecularMinimumDistances, StaticArrays

julia> sys = SelfPairs(
           xpositions=rand(SVector{3,Float64},10^5),
           cutoff=0.1,
           unitcell=[1,1,1],
           xn_atoms_per_molecule=5
       )
SelfPairs system with:

Number of atoms: 100000
Cutoff: 0.1
unitcell: [1.0, 0.0, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0, 1.0]
Number of molecules: 20000

julia> minimum_distances!(sys)
20000-element Vector{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 4, 24930, 0.008039482961077074)
 MinimumDistance{Float64}(true, 6, 74055, 0.0049818659155905255)
 ⋮
 MinimumDistance{Float64}(true, 99999, 75403, 0.0025051670801269433)
```
