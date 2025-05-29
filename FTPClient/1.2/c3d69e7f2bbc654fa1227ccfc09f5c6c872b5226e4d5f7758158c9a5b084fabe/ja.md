```
FTP(; kwargs...) -> FTP
```

FTPオブジェクトを作成します。

# キーワード

  * `hostname::AbstractString=""`: FTPサーバーのホスト名またはアドレス。
  * `username::AbstractString=""`: FTPサーバーにアクセスするために使用されるユーザー名。
  * `password::AbstractString=""`: FTPサーバーにアクセスするために使用されるパスワード。
  * `ssl::Bool=false`: セキュアなFTP接続を使用します。
  * `implicit::Bool=false`: 暗黙のセキュリティ（FTPS）を使用します。
  * `verify_peer::Bool=true`: ピアの証明書の信頼性を確認します。
  * `active_mode::Bool=false`: データ接続を確立するためにアクティブモードを使用します。
  * `verbose::Union{Bool,IOStream}=false`: LibCurlの出力をキャプチャするための`IOStream`または`Bool`。trueの場合、出力はSTDERRに書き込まれます。
