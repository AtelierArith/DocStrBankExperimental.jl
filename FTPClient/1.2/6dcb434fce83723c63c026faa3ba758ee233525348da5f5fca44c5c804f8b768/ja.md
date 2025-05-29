```
ftp_command(
    options::RequestOptions,
    cmd::AbstractString;
    verbose::Union{Bool,IOStream}=false,
)
```

非永続接続でFTPコマンドを送信します。`Response`を返します。
