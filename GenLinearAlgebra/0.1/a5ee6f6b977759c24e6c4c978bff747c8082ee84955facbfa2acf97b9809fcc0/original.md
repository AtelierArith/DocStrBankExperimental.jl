`solutionmat(mat,v)`

returns  one solution  `x` of  the equation  `transpose(mat)*x=v` (that is, expresses  `v` as a linear combination of  the rows of `mat`), or `nothing` if  no such solution  exists. Similar to  `transpose(mat)\v` when `mat` is invertible.

```julia-repl
julia> m=[2 -4 1;0 0 -4;1 -2 -1]
3×3 Matrix{Int64}:
 2  -4   1
 0   0  -4
 1  -2  -1

julia> x=solutionmat(m,[10,-20, -10])
3-element Vector{Rational{Int64}}:
   5
 15//4
   0

julia> m'*x
3-element Vector{Rational{Int64}}:
  10
 -20
 -10

julia> solutionmat(m,[10, 20, -10])
```
