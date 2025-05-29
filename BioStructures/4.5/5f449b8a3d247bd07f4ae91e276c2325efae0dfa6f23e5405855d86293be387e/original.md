```
DistanceMap(element)
DistanceMap(element_one, element_two)
DistanceMap(float_array_2D)
```

Calculate the distance map for a `StructuralElementOrList`, or between two `StructuralElementOrList`s.

This returns a `DistanceMap` type containing a `Array{Float64, 2}` with minimum distances between the sub-elements. When one element is given as input this returns a symmetric square matrix. To directly access the underlying data of `DistanceMap` `dm`, use `dm.data`.

# Examples

```julia
cbetas_A = collectatoms(struc["A"], cbetaselector)
cbetas_B = collectatoms(struc["B"], cbetaselector)

# Distance map of chain A showing how far each Cβ atom is from the others
dm = DistanceMap(cbetas_A)

# Returns the distance between the tenth and twentieth element
dm[10, 20]

# Rectangular distance map of chains A and B
dm = DistanceMap(cbetas_A, cbetas_B)

# Write the distance map to file
using DelimitedFiles
writedlm("distances.out", dm.data, " ")
```
