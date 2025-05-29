```
@register_discontinuity f(arg1, arg2, ...) root_expr left_expr right_expr
```

不連続性を持つ関数を登録するためのユーティリティマクロです。引数 `arg1, arg2, ...` を持つ関数 `f` は、`rootfunction` として `root_expr`、`left_continuous_function` として `left_expr`、および `right_continuous_function` として `right_expr` を持ちます。`root_expr`、`left_expr`、および `right_expr` はすべて `arg1, arg2, ...` に関する式です。

例えば、`max(x, y)` は `@register_discontinuity max(x, y) x - y y x` として登録できます。

参照: [`rootfunction`](@ref)
