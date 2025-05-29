```
bound_value(x) -> value
```

バウンド型オブジェクト `x` から基になる値を取得するためのゲッタ関数です。

## 例

```jldoctest
julia> val = StringFixedLength{String,3}("abc")
"abc"

julia> typeof(val)
StringFixedLength{String, 3}

julia> inner_val = bound_value(val)
"abc"

julia> typeof(inner_val)
String
```
