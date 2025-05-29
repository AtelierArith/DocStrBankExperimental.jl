`BDSymbols(n,d)`

returns  2-symbols of defect `d` and rank `n` (for Weyl types B,C,D,2D). If `d==0`  the symbols with  equal entries are  returned twice, represented as the  first entry, followed by the repetition factor 2 and an ordinal number 0 or 1, so that `BDSymbols(n, 0)` is a set of parameters for the characters of the Weyl group of type `Dₙ`.

```julia-repl
julia> BDSymbols(2,1)
5-element Vector{Vector{Vector{Int64}}}:
 [[1, 2], [0]]
 [[0, 2], [1]]
 [[0, 1, 2], [1, 2]]
 [[2], []]
 [[0, 1], [2]]

julia> BDSymbols(4,0)
13-element Vector{Vector}:
 Any[[1, 2], 2, 0]
 Any[[1, 2], 2, 1]
 [[0, 1, 3], [1, 2, 3]]
 [[0, 1, 2, 3], [1, 2, 3, 4]]
 [[1, 2], [0, 3]]
 [[0, 2], [1, 3]]
 [[0, 1, 2], [1, 2, 4]]
 Any[[2], 2, 0]
 Any[[2], 2, 1]
 [[0, 1], [2, 3]]
 [[1], [3]]
 [[0, 1], [1, 4]]
 [[0], [4]]
```
