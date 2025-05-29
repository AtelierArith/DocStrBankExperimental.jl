```
value(con_ref::ConstraintRef; result::Int = 1)
```

制約 `con_ref` の原始値を、ソルバーによって返された最新の解の結果インデックス `result` に関連付けて返します。

つまり、`con_ref` が `func`-in-`set` の制約の参照である場合、これは [`value(::GenericVariableRef)`](@ref) によって与えられた変数の値で評価された `func` の値を返します。

値を要求する前に、[`primal_status`](@ref) を使用して結果が存在するかどうかを確認してください。

関連情報: [`result_count`](@ref)。

## 注意

スカラー制約の場合、定数は `set` に移動されるため、制約の原始値には考慮されません。たとえば、制約 `@constraint(model, 2x + 3y + 1 == 5)` は `2x + 3y`-in-`MOI.EqualTo(4)` に変換されるため、この関数によって返される値は `2x + 3y` の評価です。
