```
Reflect
```

反射型文字列のためのプレースホルダー型。

# 型エイリアス

対応する型に[`type_alias`](@ref)が定義されている場合、シリアル化とパースは型名の代わりに[`type_alias`](@ref)を使用します。これは具体的な型にのみ機能します。なぜなら、エイリアスは型変数情報を含むことができないからです。

# 例

次のオプション構造体

```julia
@option struct MyOption
    type::Reflect
    name::String = "Sam"
end
```

は次のように等価です。

```toml
type = "MyOption"
name = "Sam"
```

これは異なる型のリストを定義するのに便利です。
