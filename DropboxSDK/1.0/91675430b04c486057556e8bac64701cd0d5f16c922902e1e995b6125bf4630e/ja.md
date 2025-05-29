```
calc_content_hash(
    data_channel::Union{AbstractChannel{<: AbstractVector{UInt8}},
                        AbstractVector{<: AbstractVector{UInt8}}}
)::String
```

Dropboxのアルゴリズムを使用してデータのチャンクからコンテンツハッシュを計算します。データチャネルは、データをチャンクで渡すために使用されます。結果はデータチャネルが閉じられたときに返されます。
