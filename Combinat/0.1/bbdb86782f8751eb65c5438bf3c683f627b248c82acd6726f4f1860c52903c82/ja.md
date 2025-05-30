`tally(v;dict=false)`

コレクションまたは反復可能な `v` の各要素が何回出現するかをカウントし、`elt=>count` のソートされた `Vector` を返します（StatsBase.countmap のバリアント）。デフォルトでは、`v` の要素はソート可能である必要があります。ソート不可能ですがハッシュ可能な場合は、キーワード `dict=true` を指定すると、`Dict` を使用して（はるかに遅い）ソートされていない結果を構築します。

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
