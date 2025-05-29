`Root1(c)`

`c` は `Cyc`、`Real`、または `Complex` である必要があります。`Root1(c)` は `c==E(n,e)` の場合に `E(n,e)` を返し、`c` が単位根と等しくない場合は `nothing` を返します。

```julia-repl
julia> r=Root1(-E(9,2)-E(9,5))
Root1: ζ₉⁸

julia> order(r)
9

julia> exponent(r)
8

julia> Cyc(r) # ズンブロイチ正規形は2つの単位根の和です
Cyc{Int64}: -ζ₉²-ζ₉⁵

julia> Root1(-E(9,4)-E(9,5)) # nothing
```
