```
minimum_distances!(system)
```

Function that computes the minimum distances for an initialized system, of `SelfPairs`, `CrossPairs`, or `AllPairs` types. 

The function returs a `Vector{MinimumDistance}` cor `SelfPairs` and `CrossPairs` inputs, and a Tuple of two of such vectors for the `AllPairs` input types.

This function is used as an advanced alternative from preallocated system inputs. Only a few allocations  remain on a call to `minimum_distances!`, mostly related to the launch of the multithreaded  calculations.

# Example

```julia-repl
julia> using MolecularMinimumDistances, StaticArrays

julia> sys = SelfPairs(
           xpositions = rand(SVector{3,Float64},1000), 
           unitcell=[1,1,1], 
           cutoff = 0.1, 
           xn_atoms_per_molecule=10,
       )
SelfPairs system with:

Number of atoms: 1000
Cutoff: 0.1
unitcell: [1.0, 0.0, 0.0, 0.0, 1.0, 0.0, 0.0, 0.0, 1.0]
Number of molecules: 100

julia> minimum_distances!(sys)
100-element Vector{MinimumDistance{Float64}}:
 MinimumDistance{Float64}(true, 8, 579, 0.03570387474690425)
 MinimumDistance{Float64}(true, 12, 534, 0.02850448652684309)
 ⋮
 MinimumDistance{Float64}(true, 996, 423, 0.03655145613454862)

julia> using BenchmarkTools

julia> @btime minimum_distances!($sys);
  178.468 μs (209 allocations: 22.80 KiB)
```
