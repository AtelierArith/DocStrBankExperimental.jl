`filelistall(expr::Regex, sftp::SFTPClient.SFTP, vararg...)`

# 例

sftpおよびそのすべてのサブディレクトリ内で、文字列 "2024" で始まるすべてのファイルのリストを返し、そのリスト内のすべてのファイルをダウンロードします：

```julia
using SFTPClient, OkFiles

sftp = SFTP("sftp://123.456.78.90", "myservername", "thisispassword")

download_list = filelistall(r"^2024.*", sftp)

mkpath.(joinpath.("data", "file2024", dirname.(download_list))) # 目的地のディレクトリは作成する必要があります。さもなければ `SFTPClient.download` は失敗します。

SFTPClient.download.(sftp, download_list, downloadDir="data/file2024")
```

!!! 注     `vararg` は `SFTPClient` インターフェースに従う必要があります。詳細については `OkFiles.sftpvararginterface` を参照してください。

# 例

`sftp` サーバーの "em13" フォルダー内のファイルのみを検索します：

```julia
download_list = filelistall(r"^2024.*", sftp, "em13")
```
