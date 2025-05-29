```
sftpstat(sftp::SFTP, path::AbstractString)
```

Like Julia stat, but returns a Vector of SFTPStatStructs. Note that you can only run this on directories. Can be used for checking if a file was modified, and much more.
