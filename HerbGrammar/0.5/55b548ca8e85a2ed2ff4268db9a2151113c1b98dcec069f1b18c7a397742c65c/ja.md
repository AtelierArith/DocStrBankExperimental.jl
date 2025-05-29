```
get_domain(g::AbstractGrammar, type::Symbol)::BitVector
```

特定のタイプのホールのドメインを、文法のルールの数と同じ長さの `BitVector` として返します。ビット `i` は、ルール `i` がタイプ `type` の場合にのみ `true` に設定されます。

!!! info
    この関数は文法によって定義されたプログラム空間を探索する際に集中的に使用される可能性があるため、この関数の結果は事前に計算され、[`AbstractGrammar`](@ref) の `domains` フィールドに保存されます。

