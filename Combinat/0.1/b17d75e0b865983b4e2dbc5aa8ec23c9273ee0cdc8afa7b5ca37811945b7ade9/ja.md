`partitions(n::Integer[,k])`, `npartitions(n::Integer[,k])`

`partitions` は、正の整数 `n` の分割を辞書式順序で返します（`k` が指定されている場合は `k` 部分）。`npartitions` は（より速く）分割の数を返します。

`n` の分割数はおおよそ `exp(π√(2n/3))/(4√3 n)` です。

*分割* とは、整数の分解 `n=p₁+p₂+…+pₖ` であり、`p₁≥p₂≥…≥pₖ>0` を満たし、ベクトル `p=[p₁,p₂,…,pₖ]` で表されます。`p⊢n` と書くことで、`p` が `n` の分割であることを示します。

```julia-repl
julia> npartitions(7)
15

julia> partitions(7)
15-element Vector{Vector{Int64}}:
 [1, 1, 1, 1, 1, 1, 1]
 [2, 1, 1, 1, 1, 1]
 [2, 2, 1, 1, 1]
 [2, 2, 2, 1]
 [3, 1, 1, 1, 1]
 [3, 2, 1, 1]
 [3, 2, 2]
 [3, 3, 1]
 [4, 1, 1, 1]
 [4, 2, 1]
 [4, 3]
 [5, 1, 1]
 [5, 2]
 [6, 1]
 [7]

julia> npartitions(7,3)
4

julia> partitions(7,3)
4-element Vector{Vector{Int64}}:
 [3, 2, 2]
 [3, 3, 1]
 [4, 2, 1]
 [5, 1, 1]
```

分割は、`Combinat.Partitions(n[,k])` というイテレータによって実装されており、大きな数の分割を列挙するために使用できます。
