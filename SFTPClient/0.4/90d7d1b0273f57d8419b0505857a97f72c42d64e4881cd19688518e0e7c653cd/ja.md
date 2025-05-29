```
SFTP(url::AbstractString, username::AbstractString, public_key_file::AbstractString, private_key_file::AbstractString;disable_verify_peer=false, disable_verify_host=false, verbose=false)
```

証明書認証を使用し、指定されたファイル内のキーを使用して新しいSFTPクライアントを作成します。

sftp = SFTP("sftp://mysitewhereIhaveACertificate.com", "myuser", "test.pub", "test.pem")
