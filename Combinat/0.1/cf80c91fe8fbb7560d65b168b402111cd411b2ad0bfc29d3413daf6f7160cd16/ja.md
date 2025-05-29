`compositions(n[,k];min=1)`, `ncompositions(n[,k];min=1)`

この関数は、`n` の組み合わせを返します（第二引数 `k` が与えられた場合は長さ `k` の組み合わせ）。整数 `n` の組み合わせは、整数 `≥min` の分解 `n=p₁+…+pₖ` として表され、ベクトル `[p₁,…,pₖ]` で表現されます。`k` が与えられない場合、`min` は `>0` でなければなりません。組み合わせは時々順序付き分割と呼ばれます。

`ncompositions` は（より速く）組み合わせの数を返します。整数 `≥1` の `n` の組み合わせは $2^{n-1}$ 個あり、`k` 部分 `≥1` の `n` の組み合わせは `binomial(n-1,k-1)` 個です。

```julia-repl
julia> ncompositions(4)
8

julia> compositions(4)
8-element Vector{Vector{Int64}}:
 [4]
 [1, 3]
 [2, 2]
 [3, 1]
 [1, 1, 2]
 [1, 2, 1]
 [2, 1, 1]
 [1, 1, 1, 1]

julia> ncompositions(4,2)
3

julia> compositions(4,2)
3-element Vector{Vector{Int64}}:
 [1, 3]
 [2, 2]
 [3, 1]

julia> ncompositions(4,2;min=0)
5

julia> compositions(4,2;min=0)
5-element Vector{Vector{Int64}}:
 [0, 4]
 [1, 3]
 [2, 2]
 [3, 1]
 [4, 0]
```

組み合わせは、`Combinat.Compositions(n[,k];min=1)` というイテレータによって実装されており、大きな数の組み合わせを列挙するために使用できます。
