```
SFTP(url::AbstractString, username::AbstractString;disable_verify_peer=false, disable_verify_host=false)
```

Creates a new SFTP client using certificate authentication. 

sftp = SFTP("sftp://mysitewhereIhaveACertificate.com", "myuser")

Note! You must provide the username for this to work. 

Before using this method, you must set up your certificates in ~/.ssh/id*rsa and ~/.ssh/id*rsa.pub

Of course, the host need to be in the known_hosts file as well. 

Test using your local client first: ssh myuser@mysitewhereIhaveACertificate.com

See other method if you want to use files not in ~/ssh/
