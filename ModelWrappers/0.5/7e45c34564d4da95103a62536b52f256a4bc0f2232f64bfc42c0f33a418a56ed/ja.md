```julia
struct Param{A, B}
```

ModelWrappers.jlが処理できるようにパラメータを定義するためのユーティリティ構造体です。型の安定性のためにModelWrapper構造体に分離されます。

# フィールド

  * `constraint::Any`
  * `val::Any`
