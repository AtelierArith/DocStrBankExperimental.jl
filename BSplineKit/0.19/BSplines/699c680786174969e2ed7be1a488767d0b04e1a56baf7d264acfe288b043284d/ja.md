```
has_parent_basis(::Type{<:AbstractBSplineBasis}) -> Bool
has_parent_basis(::AbstractBSplineBasis) -> Bool
```

基底が親Bスプライン基底を持つかどうかを判断するトレイトです。

これは、通常のBスプライン基底から派生した`RecombinedBSplineBasis`の場合に特に当てはまります。
