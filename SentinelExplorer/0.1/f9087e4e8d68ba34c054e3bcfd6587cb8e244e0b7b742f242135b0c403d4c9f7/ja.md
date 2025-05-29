```
get_access_token()
get_access_token(username, password)
```

提供された資格情報でデータアクセス トークンを受け取ります。

ユーザー名とパスワードは明示的に渡すことも、環境変数のペアとして提供することもできます。

後者の場合、`get_access_token()` は、ユーザー名とパスワードが環境変数 `SENTINEL_EXPLORER_USER` と `SENTINEL_EXPLORER_PASS` として提供されることを期待します。

# パラメータ

  * `username`: あなたのコペルニクス データ スペースのユーザー名。
  * `password`: あなたのコペルニクス データ スペースのパスワード。

# 戻り値

データをダウンロードするためのアクセス トークン。

# 例

```julia
token = get_access_token(ENV["SENTINEL_EXPLORER_USER"], ENV["SENTINEL_EXPLORER_PASS"])
token = get_access_token()  # 上記と同じ
```
