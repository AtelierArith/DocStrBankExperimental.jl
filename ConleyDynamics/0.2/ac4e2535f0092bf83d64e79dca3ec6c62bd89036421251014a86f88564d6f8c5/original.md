```
sc, vfG, vfC = example_dunce_chaos()
```

Create a minimal simplicial complex representation of the Dunce hat, as well as two Forman vector fields.

The function returns the simplicial representation of the Dunce hat in `sc` over the finite field `GF(2)`. The Forman vector field `vfG` is a gradient vector  field with unique connection matrix. The field `vfC` is a modification of this field which merges the critical cells of dimensions 1 and 2 into a Forman arrow. The resulting Forman vector field is no longer gradient,  and in fact exhibits Lorez-like chaos.

# Examples

```jldoctest
julia> sc, vfG, vfC = example_dunce_chaos();

julia> homology(sc)
3-element Vector{Int64}:
 1
 0
 0

julia> cmG = connection_matrix(sc, vfG);

julia> sparse_show(cmG.matrix)
[0   0   0]
[0   0   1]
[0   0   0]

julia> print(cmG.labels)
["1", "12", "128"]

julia> cmC = connection_matrix(sc, vfC);

julia> sparse_show(cmC.matrix)
[0]

julia> print(cmC.labels)
["1"]

julia> msC, psC = morse_sets(sc, vfC, poset=true);

julia> [conley_index(sc, mset) for mset in msC]
2-element Vector{Vector{Int64}}:
 [1, 0, 0]
 [0, 0, 0]

julia> psC
2×2 Matrix{Bool}:
 0  1
 0  0

julia> msC
2-element Vector{Vector{String}}:
 ["1"]
 ["12", "14", "15", "25", "28", "56", "68", "78", "124", "125", "128", "145", "256", "278", "568", "678"]
```
