```
poset_builder(objects::Vector{T}, comp_func::Function)::Poset where {T}
```

与えられた `objects` のリストと比較関数 `comp_func` を使用して、オブジェクト `i` がオブジェクト `j` より小さい場合、`comp_func(objects[i], objects[j])` が `true` を返す `Poset` を作成します。

サイクルが作成されるとエラーが発生します。
