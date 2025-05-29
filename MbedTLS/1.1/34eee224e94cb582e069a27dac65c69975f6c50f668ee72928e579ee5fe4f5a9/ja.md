```
SSLConfig(verify::Bool; log_secrets=nothing)
```

サーバーに接続するためのクライアントSSLConfigを初期化します。

`verify`がfalseの場合、証明書が有効であるかどうかを確認しません。

`log_secrets`が文字列の場合、その名前のファイルに接続の秘密を保存します。これは、デバッグ時にWiresharkでキャプチャしたトラフィックを復号化するのに便利です。
