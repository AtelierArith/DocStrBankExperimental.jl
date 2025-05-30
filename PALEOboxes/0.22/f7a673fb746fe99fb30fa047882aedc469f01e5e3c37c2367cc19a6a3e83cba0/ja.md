```
Attribute{T}
```

変数属性 `name` の定義。データ型 `T`、`default_value`、`required`（変数が作成されるときに `default_value` で追加される場合は `true`）、`units`、およびオプションの `description` を定義します。

変数属性は各変数ごとに `Dict(name => value)` として保存されるため、これらの定義はデフォルトを提供し、型をチェックし、説明的なメタデータを提供するためにのみ使用されます。

`ParseFromString` は通常 `Nothing` であるべきです：その場合、[`set_attribute!`](@ref) を呼び出すときに `Type T` の値が必要です。`ParseFromString` が `true` の場合、[`set_attribute!`](@ref) は `AbstractString` を受け入れ、`Base.parse(T, strvalue)` を呼び出して `T` に変換します。これにより、例えば、列挙型の値を持つ属性を `Attribute{EnumType, true}` として定義し、`parse(EnumType, rawvalue::AbstractString)` を実装することができます。
