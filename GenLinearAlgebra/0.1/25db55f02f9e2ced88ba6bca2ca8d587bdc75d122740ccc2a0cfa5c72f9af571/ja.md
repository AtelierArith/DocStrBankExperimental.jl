`independent_rows(m::AbstractMatrix)`

は、`m` の独立した行のセットのインデックスのベクトルを返します（そのようなセットの中で辞書式順序で最初のもの）。

```julia-repl
julia> m=[1 2;2 4;5 6]
3×2 Matrix{Int64}:
 1  2
 2  4
 5  6

julia> independent_rows(m)
2-element view(::Vector{Int64}, 1:2) with eltype Int64:
 1
 3
```
