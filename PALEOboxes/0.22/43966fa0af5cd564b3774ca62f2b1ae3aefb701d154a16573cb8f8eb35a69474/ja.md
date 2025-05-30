```
show_methods_initialize(model::Model)
```

反応初期化メソッドの順序付きリストを表示します（[`add_method_initialize!`](@ref)によって登録され、各モデルのタイムステップの開始時に[`do_deriv`](@ref)によって呼び出されます）。
