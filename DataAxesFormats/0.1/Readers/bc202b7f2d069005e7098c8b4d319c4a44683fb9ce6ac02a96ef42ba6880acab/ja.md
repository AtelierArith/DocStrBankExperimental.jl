```
get_scalar(
    daf::DafReader,
    name::AbstractString;
    [default::Union{StorageScalar, Nothing, UndefInitializer} = undef]
)::Maybe{StorageScalar}
```

`daf`内の`name`というスカラープロパティの値を取得します。

`default`が`undef`（デフォルト）の場合、最初に`name`スカラープロパティが`daf`に存在するか確認します。そうでない場合、プロパティが存在しないときは`default`が返されます。
