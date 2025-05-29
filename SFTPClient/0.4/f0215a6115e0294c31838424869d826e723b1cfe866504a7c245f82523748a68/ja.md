```
SFTP(url::AbstractString, username::AbstractString, password::AbstractString;create_known_hosts_entry=true, disable_verify_peer=false, disable_verify_host=false)
```

新しいSFTPクライアントを作成します: url: 接続するためのURL、例: sftp://mysite.com username: 使用するユーザー名 password: ユーザーのパスワード create*known*hosts_entry: known hostsに自動的にエントリを作成します

例: sftp = SFTP("sftp://test.rebex.net", "demo", "password")
