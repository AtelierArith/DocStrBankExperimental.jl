```
lc, mvf = example_clorenz()
```

Create the simplicial complex and multivector field for the example from Figure 3 in the JCD 2016 paper by Kaczynski, Mrozek, and Wanner.

The function returns the Lefschetz complex `lc` over the finite field GF(2) and the multivector field `mvf`.

# Examples

```jldoctest
julia> lc, mvf = example_clorenz();

julia> cm = connection_matrix(lc, mvf);

julia> sparse_show(cm.matrix)
[0   0   0   0   1]
[0   0   0   0   0]
[0   0   0   0   1]
[0   0   0   0   0]
[0   0   0   0   0]

julia> print(cm.labels)
["i", "ip", "g", "gm", "bc"]

julia> ms, ps = morse_sets(lc, mvf, poset=true);

julia> [conley_index(lc, mset) for mset in ms]
4-element Vector{Vector{Int64}}:
 [1, 1, 0]
 [1, 1, 0]
 [0, 1, 0]
 [0, 0, 0]

julia> ps
4×4 Matrix{Bool}:
 0  0  1  0
 0  0  1  0
 0  0  0  1
 0  0  0  0
```
