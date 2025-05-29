```
sumbit_to_braket(ts:BloqadeSchema.QuEraTaskSpecification; <keyword arguments>)
```

`BloqadeSchema.QuEraTaskSpecification` インスタンスを Braket に送信し、`AWS.AwsQuantumTask` を返します。

資格情報は、`AWS.AWSCredentials` 構造体を介して明示的に渡すか、`nothing` を渡すことで渡すことができ、その場合は標準の AWS ロケーションで資格情報が探されます。

# キーワード引数

  * `arn="arn:aws:braket:us-east-1::device/qpu/quera/Aquila"`: マシンの ARN
  * `region="us-east-1"`: マシンが存在する AWS リージョン
  * `credentials::Union{AWSCredentials, Nothing}=nothing`: ログインするために作成できる `AWS.AWSCredentials` インスタンス。

# ログ/警告/例外

資格情報が無効な場合、`"Can't find AWS credentials!"` という `message` 文字列を含む `AWS.NoCredentials` 例外がスローされます。
