```
MLFlow
```

MLFlow APIサービスの場所とバージョンを定義する基本タイプです。

# フィールド

  * `apiroot::String`: APIのルートURL、例: `http://localhost:5000/api`
  * `apiversion::Union{Integer, AbstractFloat}`: 使用されるAPIバージョン、例: `2.0`
  * `headers::Dict`: REST APIリクエストに提供されるHTTPヘッダー。
  * `username::Union{Nothing, String}`: 基本認証のためのユーザー名。
  * `password::Union{Nothing, String}`: 基本認証のためのパスワード。

!!! warning
    `username`と`password`が提供されている場合、`Authorization`ヘッダーを提供することはできません。その場合、エラーが発生します。


!!! note
      * `MLFLOW_TRACKING_URI`が設定されている場合、提供された`apiroot`は無視されます。
      * `MLFLOW_TRACKING_USERNAME`が設定されている場合、提供された`username`は無視されます。
      * `MLFLOW_TRACKING_PASSWORD`が設定されている場合、提供された`password`は無視されます。

    これらの指示は警告として表示されます。


# 例

```@example
mlf = MLFlow()
```

```@example
remote_url="https://<your-server>.cloud.databricks.com"; # リモートサーバーのアドレス
mlf = MLFlow(remote_url, headers=Dict("Authorization" => "Bearer <your-secret-token>"))
```
