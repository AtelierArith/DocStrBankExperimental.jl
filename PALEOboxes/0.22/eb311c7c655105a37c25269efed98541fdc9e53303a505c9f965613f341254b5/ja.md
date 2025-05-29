```
Parameter{T, ParseFromString}
```

型 `T` の反応パラメータ。

短い名前 `ParDouble`、`ParInt`、`ParBool`、`ParString` を使用して作成します。

値は `<par>[]` として読み取り、[`setvalue!`](@ref) で設定します。

`external=true` のパラメータは、`name` がそのリストに存在する場合、モデルレベルのパラメータリストから設定できます。

`ParseFromString` は通常 `Nothing` であるべきです：その場合、[`setvalue!`](@ref) を呼び出すときに `Type T` の値が必要です。`ParseFromString` が `Nothing` でない場合、[`setvalue!`](@ref) は `AbstractString` を受け入れ、`Base.parse(ParseFromString, strvalue)` を呼び出します。これにより、例えば列挙型の値を持つパラメータを `Parameter{EnumType, EnumType}` で定義し、`parse(EnumType, rawvalue::AbstractString)` を実装することができます。
