`symbol_partition_tuple(p, s)` は、パーティションタプル `p` の形 `s` のシンボルです。

一般的な場合、`s` は `p` と同じ長さの `Vector{Int}` であり、結果の i 番目の要素は、長さ `sᵢ` になるようにシフトされた `pᵢ` の β-集合です（これを可能にする最小の整数が `s` に追加されます）。

`s` が正の整数の場合、これは `[s,0,0,…]` と解釈され、負の整数の場合は `[0,-s,-s,…]` と解釈されます。したがって、`p` が二重パーティションであるとき、`p` に関連付けられた欠陥 `s` のシンボルが得られます。他の用途として、`G(e,1,r)` の主系列のキャラクターに対するユニポテントシンボルは、パーティションの `e`-タプル `p` によってパラメータ化され、`symbol_partition_tuple(p,1)` です。また、`G(e,e,r)` の場合、同様の計算は `symbol_partition_tuple(p,0)` です（この関数は `G(e,e,r)` のためにコーディングされた周期的な `p` を処理します）。

```julia-repl
julia> symbol_partition_tuple([[2,1],[1]],1)
2-element Vector{Vector{Int64}}:
 [1, 3]
 [1]

julia> symbol_partition_tuple([[2,1],[1]],0)
2-element Vector{Vector{Int64}}:
 [1, 3]
 [0, 2]

julia> symbol_partition_tuple([[2,1],[1]],-1)
2-element Vector{Vector{Int64}}:
 [1, 3]
 [0, 1, 3]
```
