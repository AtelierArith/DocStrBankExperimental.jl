```
upload(
    ftp::FTP,
    local_path::AbstractString,
    remote_path::AbstractString;
    ftp_options=ftp.ctxt,
    mode::FTP_MODE=binary_mode,
) -> Response
```

"local*path"で指定されたファイルを"remote*path"で指定されたファイルまたはディレクトリにアップロードします。

"remote*path"がファイルへのパスである場合、そのファイルは提供されたパスを使用してFTPにアップロードされます。"remote*path"がディレクトリへのパスである場合（つまり、"/"、"."、または".."で終わる場合）、ファイルは指定されたディレクトリにアップロードされますが、"local_path"のベース名がファイル名として使用されます。

# 引数

  * `ftp::FTP`: 配信先のFTP。詳細はFTPClient.FTPを参照してください。
  * `local_path::AbstractString`: 配信したいファイルのファイルパス。
  * `remote_path::AbstractString`: 配信先のファイル/ディレクトリパス。

# キーワード

  * `ftp_options=ftp.ctxt`: FTPオプション
  * `mode::FTP_MODE=binary_mode`: FTPモードを設定します。

# 戻り値

`FTPResponse`: FTPレスポンスオブジェクトを返します。
