```
download(
    ftp::FTP,
    file_name::AbstractString,
    save_path::AbstractString="";
    mode::FTP_MODE=binary_mode,
)
```

FTPサーバーからファイル「file*name」をダウンロードし、IOStreamを返します。「save*path」が指定されていない場合、内容はIOBufferに書き込まれ、返されます。
