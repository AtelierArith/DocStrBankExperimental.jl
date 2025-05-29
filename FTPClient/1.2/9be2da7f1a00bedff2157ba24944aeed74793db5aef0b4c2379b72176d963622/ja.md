```
upload(
    ftp::FTP,
    local_path_io::IO,
    remote_path::AbstractString;
    ftp_options=ftp.ctxt,
    mode::FTP_MODE=binary_mode,
```

) -> Response

IOオブジェクト "local*path*io" をFTPサーバーにアップロードし、"remote_path" として保存します。

# 引数

  * `ftp::FTP`: 配信先のFTP。詳細はFTPClient.FTPを参照してください。
  * `local_path_io::IO`: 配信したいIOオブジェクト。
  * `remote_path::AbstractString`: 配信先のパス。

# キーワード

  * `ftp_options=ftp.ctxt`: FTPオプション
  * `mode::FTP_MODE=binary_mode`: FTPモードを設定します。

# 戻り値

`FTPResponse`: FTPレスポンスオブジェクトを返します。
