`lnullspaceInt(m::Matrix{<:Integer})

は、`m`の整数左零空間の基底を形成する行からなる行列を返します。すなわち、整数エントリを持つ`m`の左零空間の要素です。

```julia-repl
julia> m=[1 2 7;4 5 6;7 8 9;10 11 19;5 7 12]
5×3 Matrix{Int64}:
  1   2   7
  4   5   6
  7   8   9
 10  11  19
  5   7  12

julia> MatInt.lnullspaceInt(m)
2×5 Matrix{Int64}:
 1  18   -9  2  -6
 0  24  -13  3  -7
```
