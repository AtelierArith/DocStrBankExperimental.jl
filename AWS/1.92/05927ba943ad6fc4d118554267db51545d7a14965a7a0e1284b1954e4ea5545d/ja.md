```
AWSCredentials(; profile=nothing) -> Union{AWSCredentials, Nothing}
```

提供されたプロファイルに基づいてAWSCredentialsオブジェクトを作成します（提供されていない場合は「default」が使用されます）。

認証情報の場所を次の順序でチェックします:     1. 環境変数     2. ~/.aws/credentials     3. ~/.aws/config     4. EC2またはECSメタデータ

# キーワード

  * `profile::AbstractString`: AWSCredentialsを検索するために使用される特定のプロファイル

# 例外

  * `error("Can't find AWS Credentials")`: AWSCredentialsが見つかりませんでした
