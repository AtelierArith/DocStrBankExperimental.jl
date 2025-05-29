```
print_active_bridges(
    [io::IO = stdout,]
    model::GenericModel,
    S::Type{<:MOI.AbstractSet},
)
```

変数を集合 `S` に制約を追加するために必要なブリッジのリストを印刷します。
