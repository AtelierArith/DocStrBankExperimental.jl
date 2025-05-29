```
function minimum_distances(
   xpositions::AbstractVector{<:SVector},
   # or xpositions *and* ypositions (CrossPairs or AllPairs)
   cutoff=0.1,
   unitcell=[1,1,1],
   xn_atoms_per_molecule=5
   # or xn_atoms_per_molecule (CrossPairs)
   # or xn_atoms_per_molecule *and* yn_atoms_per_molecule (AllPairs)
)
```

This function computes directly the minimum distances in a set of particles.  Depending on the number of input position arrays provided and on the number of molecular index information provided, a different type of calculation is performed:

  * If `xpositions` and `xn_atoms_per_molecule` are provided, the minimum distances within the set of molecules of the set provided are computed.
  * If `xpositions` and `ypositions` are provided, and **only** `xn_atoms_per_molecule` is provided, the minimum distance of molecule of set `x` will be computed relative to set `y` (or, in other words, `ypositions` are considered a single structure)
  * If `xpositions` and `ypositions` are provided, and `xn_atoms_per_molecule` **and** `yn_atoms_per_molecule` are given, the minimum distances of each molecule of `x` to any atom of `y` are computed, and vice-versa. A tuple of vectors of minimum distances is returned, with lengths corresponding to the number of molecules of sets `x` and `y`, respectively.

As for the other functions are constructors, the `xn_atoms_per_molecule` keyword parameters can be substituted by a general function which returns the molecular  index of the molecule of each atom (i. e. `(i) -> (i-1)%n_atoms_per_molecule + 1` in the simplest and default case).

# Examples

## Single set of molecules: all minimum distances within the set

Note that the output contains a vector of `MinimumDistance` elements with a length equal to the number of molecules of the set.

```julia-repl
julia> using MolecularMinimumDistances, StaticArrays

julia> list = minimum_distances(
           xpositions = rand(SVector{3,Float64},10^5), 
           unitcell=[1,1,1], 
           cutoff = 0.1, 
           xn_atoms_per_molecule=10)
10000-element Vector{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 5, 71282, 0.007669490894775502)
 MinimumDistance{Float64}(true, 19, 36374, 0.005280726329888545)
 ⋮
 MinimumDistance{Float64}(true, 99998, 44320, 0.006509632622462869)
```

## Two sets: minimum distances of one set relative to the other

Note that the output contains the number of molecules of the `x` set. For each molecule of this set, the minimum distance to the set `y` is  computed. This is the typical "solute-solvent" example, where `x` contains the solvent positions, and `y` contains the solute positions.

```julia-repl
julia> list = minimum_distances(
           xpositions = rand(SVector{3,Float64},10^5), 
           ypositions = rand(SVector{3,Float64},10^3),
           unitcell=[1,1,1], 
           cutoff = 0.1, 
           xn_atoms_per_molecule=10,
       )
10000-element Vector{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 5, 596, 0.025526453519907292)
 MinimumDistance{Float64}(true, 18, 391, 0.014114699969628301)
 ⋮
 MinimumDistance{Float64}(true, 99993, 289, 0.016089848937890512)
```

## Two-sets: computing all minimum distances among molecules

If the number of molecules of both sets are provided with the `xn_atoms_per_molecule` and `yn_atoms_per_molecule` keywords, both sets are split into molecules, and all minimum distances are computed. For each molecule of each set,  the minimimum distance to any other molecule of the other set is returned. The output is a tuple of lists.

```julia-repl
julia> lists = minimum_distances(
           xpositions = rand(SVector{3,Float64},10^5), 
           ypositions = rand(SVector{3,Float64},10^3),
           unitcell=[1,1,1], 
           cutoff = 0.1, 
           xn_atoms_per_molecule=10,
           yn_atoms_per_molecule=100
       );

julia> lists[1]
10000-element Vector{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 10, 471, 0.03211876310646438)
 MinimumDistance{Float64}(true, 13, 113, 0.0364141004391549)
 ⋮
 MinimumDistance{Float64}(true, 99992, 673, 0.0345818388567913)

julia> lists[2]
10-element Vector{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 81, 754, 0.002292544732548094)
 MinimumDistance{Float64}(true, 156, 17208, 0.0018147268509811352)
 ⋮
 MinimumDistance{Float64}(true, 944, 98048, 0.002902338025311851)
```
