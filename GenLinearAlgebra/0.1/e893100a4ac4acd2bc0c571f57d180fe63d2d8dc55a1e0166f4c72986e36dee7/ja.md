`rowspace(m::AbstractMatrix)`

は、`m` の行によって生成されるベクトル空間である `m` の行空間の標準形、すなわちエシェロン形を返します。これは `m` の行空間の特定の基底です：各行の最初の非ゼロ要素は 1 であり、そのような要素はその列の唯一の非ゼロ要素でもあります。整数行列は、この関数を適用する前に `Rational` に変換されます。

```julia-repl
julia> m=[1 2;2 4;5 6]
3×2 Matrix{Int64}:
 1  2
 2  4
 5  6

julia> rowspace(m)
2×2 view(::Matrix{Rational{Int64}}, 1:2, :) with eltype Rational{Int64}:
 1  0
 0  1
```
