```
dual(con_ref::ConstraintRef; result::Int = 1)
```

制約 `con_ref` の双対値を、ソルバーによって返された最新の解の結果インデックス `result` に関連付けて返します。

値を要求する前に、`has_dual` を使用して結果が存在するかどうかを確認してください。

参照: [`result_count`](@ref), [`shadow_price`](@ref).
