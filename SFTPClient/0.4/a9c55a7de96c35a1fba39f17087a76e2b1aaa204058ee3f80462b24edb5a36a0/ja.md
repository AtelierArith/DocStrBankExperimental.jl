```
SFTPClient.download(
sftp::SFTP,
file_name::AbstractString,
 output = tempname();downloadDir::Union{String, Nothing}=nothing)

 ファイルをダウンロードします。直接使用することも、ファイルに保存することもできます。 
 ダウンロードしたファイルを保存したい場合はdownloadDirを指定してください。ブロードキャスティングを使用することもできます。
例:

sftp = SFTP("sftp://test.rebex.net/pub/example/", "demo", "password")
files=readdir(sftp)
downloadDir="/tmp"
SFTPClient.download.(sftp, files, downloadDir=downloadDir)

このように使用することもできます:
df=DataFrame(CSV.File(SFTPClient.download(sftp, "/mydir/test.csv")))
```
