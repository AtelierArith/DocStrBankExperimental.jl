```
FTP(url; kwargs...)
```

URIで指定された情報を使用してFTPサーバーに接続します。

# キーワード

  * `verify_peer::Bool=true`: ピアの証明書の信頼性を確認します。
  * `active_mode::Bool=false`: データ接続を確立するためにアクティブモードを使用します。

# 例

```julia
julia> FTP("ftp://user:password@ftp.example.com");  # セキュリティなしのFTP接続

julia> FTP("ftpes://user:password@ftp.example.com");  # 明示的なセキュリティ (FTPES)

julia> FTP("ftps://user:password@ftp.example.com");  # 暗黙的なセキュリティ (FTPS)
```
