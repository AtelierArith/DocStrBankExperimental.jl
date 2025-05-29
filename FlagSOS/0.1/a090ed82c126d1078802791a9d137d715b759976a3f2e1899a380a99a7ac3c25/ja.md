```
generateAll(::Type{F}, maxVertices::Int, maxPredicates::Vector{Int}; withProperty = (F::T) -> true) where {F}
```

タイプ `F` のすべてのフラグを生成し、最大 `maxVertices` 頂点および最大 `maxPredicates` 非ゼロ述語値を持ちます。 'maxPredicates' は、複数の述語がある場合のためのベクトルです。関数 `withProperty:F->{true, false}` が与えられた場合、プロパティが保持される限り、フラグにエッジを追加し続けます。
