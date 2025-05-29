```
download(
    ftp::FTP,
    file_name::AbstractString,
    save_path::AbstractString="";
    mode::FTP_MODE=binary_mode,
)
```

Download the file "file*name" from FTP server and return IOStream. If "save*path" is not specified, contents are written to and returned as an IOBuffer.
