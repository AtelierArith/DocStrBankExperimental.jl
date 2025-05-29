```
Logger
```

`Logger`は、msg文字列を`Records`に変換し、それを各ハンドラーに渡す役割を担います。デフォルトでは、ロガーはそのメッセージを親ロガーに伝播させます。

# フィールド

  * `name::AbstractString`: ロガーの名前です（必須）。
  * `handlers::Dict{Any, Handler}`: `Handler`のコレクションです（デフォルトは空の`Dict`）。
  * `level::AbstractString`: ハンドラーにメッセージをログするためのロガーの現在の最小ログレベルです（デフォルトは"not_set"）。
  * `levels::Dict{AbstractString, Int}`: 利用可能なログレベルをその相対的な優先度（整数値で表現）にマッピングしたものです（デフォルトは`Memento._log_levels`を使用）。
  * `record::Type`: このロガーによって生成されるべき`Record`タイプです（デフォルトは`DefaultRecord`）。
  * `propagate::Bool`: このロガーがそのメッセージを親に伝播させるべきかどうかです（デフォルトは`true`）。
