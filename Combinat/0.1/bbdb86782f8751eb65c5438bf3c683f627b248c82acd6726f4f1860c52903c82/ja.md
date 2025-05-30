`tally(v;dict=false)`

は、コレクションまたはイテラブル `v` の各要素が何回出現するかをカウントし、ソートされた `Vector` の `elt=>count` を返します（StatsBase.countmap のバリアント）。デフォルトでは、`v` の要素はソート可能である必要があります。もしソート不可能ですがハッシュ可能な場合は、キーワード `dict=true` を指定することで、`Dict` を使用して（はるかに遅い）ソートされていない結果を構築します。

```julia-repl
julia> tally("a tally test")
7-element Vector{Pair{Char, Int64}}:
 ' ' => 2
 'a' => 2
 'e' => 1
 'l' => 2
 's' => 1
 't' => 3
 'y' => 1
```
