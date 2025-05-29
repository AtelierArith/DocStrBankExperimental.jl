```
AWSCredentials
```

AWSと対話する際には、あなたが誰であるか、要求しているリソースにアクセスする権限があるかを確認するために、[AWSセキュリティ認証情報](http://docs.aws.amazon.com/general/latest/gr/aws-security-credentials.html)を指定します。AWSはセキュリティ認証情報を使用して、リクエストを認証および承認します。フィールド`access_key_id`と`secret_key`は、APIリクエストを認証するために使用されるアクセスキーを保持します（[アクセスキーの作成、変更、および表示](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html#Using_CreateAccessKey)を参照）。[一時的なセキュリティ認証情報](http://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp.html)は、追加のセッション`token`フィールドを必要とします。`user_arn`および`account_number`フィールドは、[`aws_user_arn`](@ref)および[`aws_account_number`](@ref)関数の結果をキャッシュするために使用されます。

AWS.jlは複数の場所で認証情報を検索し、認証情報が見つかると停止します。認証情報の優先順位は主に[AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-authentication.html#cli-chap-authentication-precedence)を反映しており、次のようになります：

1. `AWSCredentials`に直接渡された認証情報またはプロファイル
2. [環境変数](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-envvars.html)
3. [Webアイデンティティ](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-role.html#cli-configure-role-oidc)
4. AWS構成ファイルを介して提供される[AWSシングルサインオン（SSO）](http://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sso.html)
5. [AWS認証情報ファイル](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html)（例："~/.aws/credentials"）
6. AWS構成ファイルの`credential_process`で設定された[外部プロセス](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-sourcing-external.html)
7. AWS構成ファイルの`aws_access_key_id`で設定された[AWS構成ファイル](http://docs.aws.amazon.com/cli/latest/userguide/cli-config-files.html)
8. [Amazon ECSコンテナ認証情報](https://docs.aws.amazon.com/AmazonECS/latest/developerguide/task-iam-roles.html)
9. [Amazon EC2インスタンスメタデータ](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html)

認証情報が見つかると、それらにアクセスした方法が`renew`フィールドに保存され、期限が切れる日時が`expiry`フィールドに保存されます。これにより、[`check_credentials`](@ref)を使用して必要に応じて認証情報を更新できます。`renew`が`nothing`に設定されている場合、認証情報を更新する試みは行われません。更新関数は、失敗時には`nothing`を返し、成功時にはポピュレートされた`AWSCredentials`オブジェクトを返すことが期待されます。返された`AWSCredentials`の`renew`フィールドは破棄され、設定する必要はありません。

`~/.aws/credentials`から使用するプロファイルを指定するには、例えば`AWSCredentials(profile="profile-name")`を実行します。
