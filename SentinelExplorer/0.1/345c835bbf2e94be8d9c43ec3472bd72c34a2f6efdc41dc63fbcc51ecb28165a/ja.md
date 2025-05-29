```
authenticate(username, password)
```

Copernicus Data Spaceの認証情報で認証します。

環境変数`SENTINEL_EXPLORER_USER`と`SENTINEL_EXPLORER_PASS`を設定し、今後のリクエストの認証に使用されます。

# パラメータ

  * `username`: あなたのCopernicus Data Spaceのユーザー名。
  * `password`: あなたのCopernicus Data Spaceのパスワード。

# 例

```julia
authenticate("my_username", "my_password")
token = get_access_token()
```
