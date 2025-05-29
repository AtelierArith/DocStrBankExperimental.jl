```
FileRoller <: IO
```

ロールログファイルを管理する責任があります。

# フィールド

  * `prefix::AbstractString`: ログのファイル名プレフィックス。
  * `folder::AbstractString`: ログを書き込むディレクトリ。
  * `filepath::AbstractString`: ログの完全なファイルパス。
  * `file::IO`: 現在のファイルIOハンドル。
  * `byteswritten::Int64`: 現在のファイルに書き込まれたバイト数を追跡します。
  * `max_sz::Int`: 別のファイルにロールオーバーする前にファイルに書き込まれる最大バイト数。
