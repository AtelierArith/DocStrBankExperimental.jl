```
set_scalar!(
    daf::DafWriter,
    name::AbstractString,
    value::StorageScalar;
    [overwrite::Bool = false]
)::Nothing
```

`daf`内の`name`を持つスカラープロパティの`value`を設定します。

`overwrite`（デフォルト）は`false`の場合、最初に`name`スカラープロパティが存在しないことを確認します。
