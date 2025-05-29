`shiftβ( β, n)` は β-セット `β` を `n` だけシフトします。

```julia-repl
julia> shiftβ([2,3],2)
4-element Vector{Int64}:
 0
 1
 4
 5

julia> shiftβ([0,1,4,5],-2)
2-element Vector{Int64}:
 2
 3

```
