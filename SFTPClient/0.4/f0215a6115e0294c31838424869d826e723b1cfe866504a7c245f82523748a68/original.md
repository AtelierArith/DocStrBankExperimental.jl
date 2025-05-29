```
SFTP(url::AbstractString, username::AbstractString, password::AbstractString;create_known_hosts_entry=true, disable_verify_peer=false, disable_verify_host=false)
```

Creates a new SFTP Client: url: The url to connect to, e.g., sftp://mysite.com username: The username to use password: The users password create*known*hosts_entry: Automatically create an entry in known hosts

Example: sftp = SFTP("sftp://test.rebex.net", "demo", "password")
