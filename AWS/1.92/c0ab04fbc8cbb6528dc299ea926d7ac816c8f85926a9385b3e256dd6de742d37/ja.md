```
sso_credentials(profile=nothing) -> Union{AWSCredentials, Nothing}
```

AWS 設定ファイル内の `profile` に定義された AWS シングルサインオン (SSO) 設定を介して資格情報を取得します。`profile` に対する SSO 設定が見つからない場合は、`nothing` が返されます。

# 引数

  * `profile`: `AWSCredentials` を取得するために使用される特定のプロファイル、デフォルトは `nothing`
