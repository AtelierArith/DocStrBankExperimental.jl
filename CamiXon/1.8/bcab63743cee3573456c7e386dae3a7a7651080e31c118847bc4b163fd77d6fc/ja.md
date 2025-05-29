```
Value(val::Real, unit::String)
```

実数値と単位指定子を保持するオブジェクトです。

フィールドは次の通りです：

  * `.val`: 数値 (`::Real`)
  * `.unit`: 単位指定子 (`::String`)

#### 例：

```
julia> f = Value(1,"Hz")
Value(1, "Hz")

julia> f.val
1

julia> f.unit
"Hz"
```
