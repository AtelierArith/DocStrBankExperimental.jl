```
ftp_get(
    ctxt::ConnContext,
    file_name::AbstractString,
    save_path::AbstractString="";
    mode::FTP_MODE=binary_mode,
)
```

持続的な接続でファイルをダウンロードします。`Response`を返します。

# 引数

  * `ctxt::ConnContext`: ftp_connectを介して定義された接続オプションを含みます。詳細については`RequestOptions`を参照してください。
  * `file_name::AbstractString`: サーバー上のファイルへのパス。
  * `save_path::AbstractString=""`: 指定されていない場合、ファイルは`Response`のボディに書き込まれます。
  * `mode::FTP_MODE=binary_mode`: ファイルがバイナリまたはASCII形式で転送されるかどうかを定義します。
