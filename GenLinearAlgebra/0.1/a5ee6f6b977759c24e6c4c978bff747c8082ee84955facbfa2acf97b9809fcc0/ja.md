`solutionmat(mat,v)`

は、方程式 `transpose(mat)*x=v` の一つの解 `x` を返します（つまり、`v` を `mat` の行の線形結合として表現します）。そのような解が存在しない場合は `nothing` を返します。`mat` が可逆であるときの `transpose(mat)\v` に似ています。

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
