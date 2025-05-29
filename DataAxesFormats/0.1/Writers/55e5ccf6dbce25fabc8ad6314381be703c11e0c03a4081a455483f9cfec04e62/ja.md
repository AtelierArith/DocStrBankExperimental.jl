```
delete_scalar!(
    daf::DafWriter,
    name::AbstractString;
    must_exist::Bool = true,
)::Nothing
```

`daf`から`name`というスカラー属性を削除します。

`must_exist`（デフォルト）であれば、最初に`daf`に`name`スカラー属性が存在することを確認します。
