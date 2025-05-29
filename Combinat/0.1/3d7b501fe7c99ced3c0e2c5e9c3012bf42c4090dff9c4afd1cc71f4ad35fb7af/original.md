`diagblocks(M::Matrix)`

`M`  should  be  a  square  matrix.  Define  a  graph  `G`  with vertices `1:size(M,1)` and with an edge between `i`  and `j` if either `M[i,j]` or `M[j,i]` is not zero or `false`. `diagblocks` returns a vector of vectors `I`  such that  `I[1]`,`I[2]`, etc..  are the  vertices in each connected component  of `G`.  In other  words, `M[I[1],I[1]]`,`M[I[2],I[2]]`,etc... are diagonal blocks of `M`.

```julia-repl
julia> m=[0 0 0 1;0 0 1 0;0 1 0 0;1 0 0 0]
4×4 Matrix{Int64}:
 0  0  0  1
 0  0  1  0
 0  1  0  0
 1  0  0  0

julia> diagblocks(m)
2-element Vector{Vector{Int64}}:
 [1, 4]
 [2, 3]

julia> m[[1,4,2,3],[1,4,2,3]]
4×4 Matrix{Int64}:
 0  1  0  0
 1  0  0  0
 0  0  0  1
 0  0  1  0
```
