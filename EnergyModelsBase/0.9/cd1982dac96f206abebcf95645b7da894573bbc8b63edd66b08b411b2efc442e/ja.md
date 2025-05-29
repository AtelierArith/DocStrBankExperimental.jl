```
outputs(n::Node)
outputs(n::Node, p::Resource)
```

ノード `n` の出力リソースを、フィールド `output` を介して指定します。

リソース `p` が指定されている場合、値を返します（[`Availability`](@ref) の場合は 1、[`Sink`](@ref) の場合は何も返しません）。
