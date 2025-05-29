```
SFTP(url::AbstractString, username::AbstractString, public_key_file::AbstractString, private_key_file::AbstractString;disable_verify_peer=false, disable_verify_host=false, verbose=false)
```

Creates a new SFTP client using certificate authentication, and keys in the files specified

sftp = SFTP("sftp://mysitewhereIhaveACertificate.com", "myuser", "test.pub", "test.pem")
