```
value(v::GenericQuadExpr; result::Int = 1)
```

`v` に関連付けられた `GenericQuadExpr` の値を、ソルバーによって返された最新の解の結果インデックス `result` で返します。

ほとんどの使用ケースに対して `getvalue` の代わりになります。

参照: [`result_count`](@ref).
