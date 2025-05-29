`solutionmatInt(mat::Matrix{<:Integer}, v::Vector{<:Integer})`

は、方程式 `mat'*x=v` の解である整数ベクトル `x` を返します。該当するベクトルが存在しない場合は `nothing` を返します。

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
