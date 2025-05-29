```
submit_to_braket(h::BloqadeExpr.RydbergHamiltonian, translation_params::BloqadeSchema.SchemaTranslationParams; <keyword arguments>)
```

`BloqadeExpr.RydbergHamiltonian` インスタンスを、ショット数とデバイスの能力を含む `BloqadeSchema.SchemaTranslationParams` と共に Braket に送信します。ハミルトニアンをハードウェアが実行できる形式に変換し、送信すると `AWS.AwsQuantumTask` が返されます。

資格情報は、`AWS.AWSCredentials` 構造体を通じて明示的に渡すことができるか、`nothing` を渡すことで、標準の AWS ロケーションで資格情報が探されます。

# キーワード引数

  * `arn="arn:aws:braket:us-east-1::device/qpu/quera/Aquila"`: マシンの ARN
  * `region="us-east-1"`: マシンが存在する AWS リージョン
  * `credentials::Union{AWSCredentials, Nothing}=nothing`: ログインするために作成できる `AWS.AWSCredentials` インスタンス。

# ログ/警告/例外

資格情報が無効な場合、`AWS.NoCredentials` 例外がスローされ、`message` 文字列 "Can't find AWS credentials!" が含まれます。

[`hardware_transform`](@ref) は常に内部で呼び出されるため、そのデバッグログも常に出力され、`h` の元の波形とハードウェアに適合する新しく生成された波形との間の差（エラー）や、原子位置の同じ変換が含まれます。
