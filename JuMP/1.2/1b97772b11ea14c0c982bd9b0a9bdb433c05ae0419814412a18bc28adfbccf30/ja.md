```
callback_value(cb_data, expr::Union{GenericAffExpr, GenericQuadExpr})
```

コールバック内のアフィンまたは二次式の原始解を返し、式に現れる各変数の値を取得します。

`cb_data` はコールバック関数への引数であり、その型はソルバーに依存します。
