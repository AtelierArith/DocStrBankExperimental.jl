```
delete_axis!(
    daf::DafWriter,
    axis::AbstractString;
    must_exist::Bool = true,
)::Nothing
```

`daf`から`axis`を削除します。これにより、この軸に基づくベクトルまたは行列のプロパティも削除されます。

`must_exist`（デフォルト）の場合、最初に`axis`が`daf`に存在することを確認します。
