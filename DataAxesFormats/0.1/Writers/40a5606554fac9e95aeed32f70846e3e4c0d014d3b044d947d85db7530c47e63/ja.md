```
delete_vector!(
    daf::DafWriter,
    axis::AbstractString,
    name::AbstractString;
    must_exist::Bool = true,
)::Nothing
```

`daf`から特定の`axis`に対して特定の`name`を持つベクトルプロパティを削除します。

最初に、`axis`が`daf`に存在することと、プロパティ名が`name`でないことを確認します。`must_exist`（デフォルト）であれば、`axis`に対して`name`ベクトルが存在することも確認します。
