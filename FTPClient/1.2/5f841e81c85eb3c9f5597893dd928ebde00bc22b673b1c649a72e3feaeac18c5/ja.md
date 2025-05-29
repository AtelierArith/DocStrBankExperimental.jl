```
ftp_put(
    ctxt::ConnContext,
    file_name::AbstractString,
    file::IO;
    mode::FTP_MODE=binary_mode,
)
```

持続的な接続でファイルをアップロードします。`Response`を返します。

# 引数

  * `ctxt::ConnContext`: ftp_connectを介して定義された接続オプションを含みます。詳細については`RequestOptions`を参照してください。
  * `file_name::AbstractString`: サーバー上のファイルのパス。
  * `file::IO`: サーバーに書き込まれるもの。
  * `mode::FTP_MODE=binary_mode`: ファイルがバイナリ形式またはASCII形式で転送されるかどうかを定義します。
