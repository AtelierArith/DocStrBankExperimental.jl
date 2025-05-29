```
ecs_instance_credentials() -> Union{AWSCredentials, Nothing}
```

ECS認証エンドポイントから資格情報を取得します。ECS認証エンドポイントが利用できない場合は、`nothing`が返されます。

詳細情報は以下をご覧ください：

  * https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-iam-roles.html
  * https://docs.aws.amazon.com/sdkref/latest/guide/feature-container-credentials.html

# 戻り値

  * `AWSCredentials`: `ECS`資格情報URIからのAWSCredentials、Env Varが設定されていない場合は`nothing`（ECSコンテナインスタンスで実行されていない）

# 例外

  * `StatusError`: レスポンスステータスが>= 300の場合
  * `ParsingError`: 無効なHTTPリクエストターゲット
