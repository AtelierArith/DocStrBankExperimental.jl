```
NamedValue(val::Value, name::String, comment::String)
```

[`Value`](@ref) とその `symbolic name` および `short` 説明を保持するオブジェクト

フィールドは次のとおりです：

  * `.val`: 値 (`::Value`)
  * `.name`: シンボリック名 (`::String`)
  * `.comment`: 説明 (`::String`)

Named Value オブジェクト `NamedValue` は、[`castNamedValue`](@ref) を使用して作成するのが最適です。

#### 例：

```
julia> f = Value(1,"Hz")
Value(1, "Hz")

julia> f = castNamedValue(f, name="frequency", comment="comment")
NamedValue(Value(1, "Hz"), "frequency", "comment")

julia> f.name
"frequency"
```
