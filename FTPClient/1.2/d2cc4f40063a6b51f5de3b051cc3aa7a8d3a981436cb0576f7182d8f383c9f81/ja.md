```
ftp_put(
    options::RequestOptions,
    file_name::AbstractString,
    file::IO;
    mode::FTP_MODE=binary_mode,
    verbose::Union{Bool,IOStream}=false,
)
```

非永続接続でファイルをアップロードします。レスポンスを返します。

# 引数

  * `options::RequestOptions`: 接続オプション。詳細は `RequestOptions` を参照してください。
  * `file_name::AbstractString`: サーバー上のファイルのパス。
  * `file::IO`: サーバーに書き込まれる内容。
  * `mode::FTP_MODE=binary_mode`: ファイルがバイナリまたはASCII形式で転送されるかどうかを定義します。
  * `verbose::Union{Bool,IOStream}=false`: LibCurlの出力をキャプチャするための `IOStream` または `Bool`。trueの場合、出力はSTDERRに書き込まれます。
