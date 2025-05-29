```
authenticate(username, password)
```

USGS Earth Explorerの認証情報で認証します。

環境変数`LANDSAT_EXPLORER_USER`と`LANDSAT_EXPLORER_PASS`を設定し、今後のリクエストの認証に使用されます。

# パラメータ

  * `username`: あなたのUSGS Earth Explorerのユーザー名。
  * `password`: あなたのUSGS Earth Explorerのパスワード。

# 例

```julia
authenticate("my_username", "my_password")
```
