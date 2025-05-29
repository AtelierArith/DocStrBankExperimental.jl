```
has_vector(daf::DafReader, axis::AbstractString, name::AbstractString)::Bool
```

`daf`の`axis`に対して、`name`という名前のベクトルプロパティが存在するかどうかを確認します。これは特別な`name`プロパティに対しては常に真です。

まず、`daf`に`axis`が存在することを確認します。
