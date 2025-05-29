```
upload(sftp::SFTP, file_name::AbstractString)
```

Upload (put) a file to the server. Broadcasting can be used too. 

files=readdir() upload.(sftp,files)
