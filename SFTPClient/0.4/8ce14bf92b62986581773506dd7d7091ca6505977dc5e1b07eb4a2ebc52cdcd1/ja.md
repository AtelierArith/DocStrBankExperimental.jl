```
SFTP(url::AbstractString, username::AbstractString;disable_verify_peer=false, disable_verify_host=false)
```

証明書認証を使用して新しいSFTPクライアントを作成します。

sftp = SFTP("sftp://mysitewhereIhaveACertificate.com", "myuser")

注意！これが機能するためには、ユーザー名を提供する必要があります。

このメソッドを使用する前に、~/.ssh/id*rsa と ~/.ssh/id*rsa.pub に証明書を設定する必要があります。

もちろん、ホストはknown_hostsファイルにも存在する必要があります。

まずはローカルクライアントを使用してテストしてください: ssh myuser@mysitewhereIhaveACertificate.com

~/ssh/ にないファイルを使用したい場合は他のメソッドを参照してください。
