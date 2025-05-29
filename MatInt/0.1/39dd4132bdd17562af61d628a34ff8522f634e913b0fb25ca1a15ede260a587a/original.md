`solutionmatInt(mat::Matrix{<:Integer}, v::Vector{<:Integer})`

returns  an  integral  vector  `x`  that  is  a  solution  of  the equation `mat'*x=v`. It returns `nothing` if no such vector exists.

```julia-repl
julia> mat=[1 2 7;4 5 6;7 8 9;10 11 19;5 7 12]
5×3 Matrix{Int64}:
  1   2   7
  4   5   6
  7   8   9
 10  11  19
  5   7  12

julia> solutionmatInt(mat,[95,115,182])
5-element Vector{Int64}:
  2285
 -5854
  4888
 -1299
     0
```
