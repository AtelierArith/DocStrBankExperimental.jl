`permutations(n)`

は、`1:n` の順列を辞書式順序で返します。これは `arrangements(1:n,n)` のより高速なバージョンです。`permutations` は、数が大きい順列を列挙するために使用できるイテレータ `Combinat.Permutations` によって実装されています。

```julia-repl
julia> permutations(3)
6-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [1, 3, 2]
 [2, 1, 3]
 [2, 3, 1]
 [3, 1, 2]
 [3, 2, 1]

julia> sum(first(p) for p in Combinat.Permutations(5))
360
```
