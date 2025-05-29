```
Syslog <: IO
```

`Syslog` は、ローカル（libc インターフェース）およびリモート（UDP / TCP ソケット）syslog サーバーへのログの書き込みを処理します。

# フィールド

  * `address::Union{Tuple{IPAddr, Int}, Nothing}`: リモートサーバーのホストと IP。`nothing` の場合はローカルにログを記録します。
  * `facility::Symbol`: 書き込む syslog ファシリティ（例: :local0, :ft, :daemon など）（デフォルトは :user）
  * `socket::Union{Base.LibuvStream, Nothing}`: メッセージをログするための UDP または TCP ソケット。`nothing` の場合はローカルにログを記録します。
