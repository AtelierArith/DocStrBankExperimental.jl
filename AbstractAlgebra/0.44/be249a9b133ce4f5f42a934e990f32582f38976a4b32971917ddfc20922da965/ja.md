```
quo(m::FPModule{T}, subm::FPModule{T}) where T <: RingElement
```

モジュール `m` の商 `M` を、モジュール `subm` によって返します（`subm` は `m` の部分モジュールとして（推移的に）構築されているか、`m` 自身でなければなりません）と、`m` から `M` への標準的な商写像を返します。
