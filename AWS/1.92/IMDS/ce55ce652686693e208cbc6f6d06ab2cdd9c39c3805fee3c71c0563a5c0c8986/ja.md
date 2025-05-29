```
IMDS
```

AWSインスタンスメタデータをインスタンスメタデータサービス（IMDS）を介して取得するためのフロントエンド。利用可能なメタデータの詳細については、公式AWSドキュメントの["インスタンスメタデータとユーザーデータ"](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html)を参照してください。

IMDSモジュールは、IMDSv1またはIMDSv2を使用するインスタンスをサポートしています（セキュリティ上の理由からIMDSv2を優先します）。
