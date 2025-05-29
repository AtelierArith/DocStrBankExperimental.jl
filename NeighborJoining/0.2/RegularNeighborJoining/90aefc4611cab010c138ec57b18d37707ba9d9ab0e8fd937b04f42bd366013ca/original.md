```
regNJ(d::AbstractMatrix{<:Number})
```

regNJ algorithm is the traditional NeighborJoining algorithm from 

> Saitou, N. & Nei, M. The neighbor-joining method: a new method for reconstructing phylogenetic trees. Molecular Biology and Evolution 4, 406-425 (1987).


This algorithm is guarenteed to infer the tree for additive distance matrices, but it does have an algorithmic complexity of `O(n^3)`, so it can be slow for distance matrices on the order of >10³.

args:

  * d is an n by n square symetric distance matrix

returns:

  * NJClust struct with fields merges and heights

examples:

```@jldoctest
julia> d = [
           0  5  9  9 8
           5  0 10 10 9
           9 10  0  8 7
           9 10  8  0 3
           8  9  7  3 0
       ];

julia> njclusts = regNJ(d)
NJClust{Int64, Float64}([-2 -1; -3 1; -4 2; -5 3], [3.0 2.0; 4.0 3.0; 2.0 2.0; 0.5 0.5])

julia> nwstring = newickstring(njclusts)
"(5:5.000000e-01,(4:2.000000e+00,(3:4.000000e+00,(2:3.000000e+00,1:2.000000e+00):3.000000e+00):2.000000e+00):5.000000e-01):0.000000e+00;"
```
