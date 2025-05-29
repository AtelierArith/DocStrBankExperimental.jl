`traces_words_mats(mats,words)`

given  a list `mats`  of matrices and  a list `words`  of words returns the list  of traces of the corresponding products of the matrices. Each subword is evaluated only once.

```julia-repl
julia> R=[[-1 -1 0 0; 0 1 0 0; 0 0 1 0; 0 0 0 1], [1 0 0 0; -1 -1 -1 0; 0 0 1 0; 0 0 0 1], [1 0 0 0; 0 1 0 0; 0 -2 -1 -1; 0 0 0 1], [1 0 0 0; 0 1 0 0; 0 0 1 0; 0 0 -1 -1]]; # 17th representation of F4

julia> words=[[], [1,2,3,4,1,2,3,4,1,2,3,4,1,2,3,4,1,2,3,4], [2,3,2,3], [2,1], [1,2,3,4,2,3,2,3,4,3], [1,2,3,4,1,2,3,4,1,2,3,4], [4,3], [1,2,1,3,2,3,1,2,3,4], [1,2,3,4,1,2,3,4,1,2,3,4,1,2,3,4], [1,2,3,4,1,2,3,4], [1,2,3,4], [1], [2,3,2,3,4,3,2,3,4], [1,4,3], [4,3,2], [2,3,2,1,3], [3], [1,2,1,3,2,1,3,2,3], [2,1,4], [3,2,1], [2,4,3,2,3], [1,3], [3,2], [1,2,3,4,1,2,3,4,1,2,3,4,2,3], [1,2,3,4,2,3]];

julia> [traces_words_mats(R,words)] # 17th character of F4
1-element Vector{Vector{Int64}}:
 [4, 0, 0, 1, -1, 0, 1, -1, -2, 2  …  0, 2, -2, -1, 1, 0, 0, 2, -2, 0]
```
