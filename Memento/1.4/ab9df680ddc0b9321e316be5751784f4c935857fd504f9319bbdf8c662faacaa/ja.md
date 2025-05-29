```
DefaultRecord <: AttributeRecord
```

最も一般的なログイベント情報を格納します。注意：より多くのログ属性が必要な場合は、次のことができます。

1. DefaultRecordに追加し、新しい属性がほとんどのアプリケーションに適用可能であればプルリクエストを開く。
2. カスタム`Record`タイプを作成する。

# フィールド

  * `date::Attribute{DateTime}`: ログイベントのタイムスタンプ
  * `level::Attribute{AbstractString}`: ログレベル
  * `levelnum::Attribute{Int}`: ログレベルの整数値
  * `msg::Attribute{AbstractString}`: ログメッセージ自体
  * `name::Attribute{AbstractString}`: ソースロガーの名前
  * `pid::Attribute{Int}`: ログイベントが発生した場所のpid
  * `threadid::Attribute{Int}`: ログイベントが発生した場所のスレッドid
  * `lookup::Attribute{StackFrame}`: 最上位のStackFrame
  * `stacktrace::Attribute{StackTrace}`: スタックトレース
