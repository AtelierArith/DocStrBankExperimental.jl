```
inputs(n::Node)
inputs(n::Node, p::Resource)
```

ノード `n` の入力リソースを、フィールド `input` を介して指定されたものとして返します。

リソース `p` が指定されている場合、[`Availability`](@ref) の場合は値 (1) を、[`Source`](@ref) の場合は何も返しません。
