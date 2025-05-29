`baseInt(m::Matrix{<:Integer})`

は、`m` の行の整数線形結合の集合、すなわち `m` の整数行空間の基底を形成する行を持つ、エルミート正規形の行列を返します。

```julia-repl
julia> m=[1 2 7;4 5 6;10 11 19]
3×3 Matrix{Int64}:
  1   2   7
  4   5   6
 10  11  19

julia> baseInt(m)
3×3 Matrix{Int64}:
 1  2   7
 0  3   7
 0  0  15
```
