```
AllPairs(;
    xpositions::AbstractVector{<:AbstractVector{<:Real}},
    ypositions::AbstractVector{<:AbstractVector{<:Real}},
    cutoff::Real,
    unitcell::AbstractVecOrMat,
    xn_atoms_per_molecule::Integer,
    yn_atoms_per_molecule::Integer,
    parallel::Bool=true
)
```

Initializes a particle system for the calculation of minimum distances between one molecule and a set of other molecules. Returns a list  minimum distances (`MinimumDistance` type), containing for each molecule of the set the information about the closest distance to the reference molecule.

Instead of the number of atoms per molecule, the user can also provide a  more general `xmol_indices` and/or `ymol_indices` functions,  which, for each atomic index, returns the corresponding molecular index (which is `mol_indices(i) = (i-1)%n + 1` where `n` is the number of atoms per molecule if all molecules have the same number of atoms and are continously stored in the array of positions). 

# Examples

```julia-repl
julia> using MolSimToolkit, StaticArrays

julia> sys = AllPairs(
           xpositions=rand(SVector{3,Float64},10^5), # "solvent" (set of molecules)
           ypositions=rand(SVector{3,Float64},1000), # "solute" (target structure)
           cutoff=0.1,
           unitcell=[1,1,1],
           xn_atoms_per_molecule=5, # of the "solvent"
           yn_atoms_per_molecule=10 # of the "solvent"
       )
AllPairs system with:

Number of atoms of first set: 100000
Number of molecules in first set: 20000

Number of atoms of second set: 1000
Number of molecules in second set: 100

Cutoff: 0.1
unitcell: [1.0, 0.0, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0, 1.0]

julia> minimum_distances!(sys)[1]
20000-element Vector{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 1, 859, 0.037219109441123784)
 MinimumDistance{Float64}(true, 10, 117, 0.042183794688796634)
 ⋮
 MinimumDistance{Float64}(true, 99996, 168, 0.014269620784984633)
```
