```
show_methods_do(model::Model)
```

反応の do メソッドの順序付きリストを表示します（[`add_method_do!`](@ref) によって登録され、各モデルのタイムステップで [`do_deriv`](@ref) によって呼び出されます）。
