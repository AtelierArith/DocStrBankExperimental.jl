```
print_active_bridges(
    [io::IO = stdout,]
    model::GenericModel,
    F::Type,
    S::Type{<:MOI.AbstractSet},
)
```

型 `F`-in-`S` の制約に必要なブリッジのリストを出力します。
