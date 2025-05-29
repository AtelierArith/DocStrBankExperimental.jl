```
RequestOptions(; kwargs...)
```

FTPサーバーに接続するために使用されるオプション。

# キーワード

  * `hostname::AbstractString="localhost"`: FTPサーバーのホスト名またはアドレス。
  * `username::AbstractString=""`: FTPサーバーにアクセスするために使用されるユーザー名。
  * `password::AbstractString=""`: FTPサーバーにアクセスするために使用されるパスワード。
  * `implicit::Bool=false`: 暗黙のFTPS構成を使用します。
  * `ssl::Bool=false`: セキュアな接続を使用します。通常、明示的FTPSに指定されます。
  * `verify_peer::Bool=true`: ピアの証明書の真正性を確認します。
  * `active_mode::Bool=false`: データ接続を確立するためにアクティブモードを使用します。
