```
submit_to_braket(h::BloqadeExpr.Hamiltonian, n_shots::Int; <keyword arguments>)
```

`BloqadeExpr.RydbergHamiltonian` インスタンスを Braket に送信し、`n_shots` はハミルトニアンを実行する回数を定義します。

資格情報は、`AWS.AWSCredentials` 構造体を介して明示的に渡すか、`nothing` を渡すことで提供できます。この場合、資格情報は標準の AWS ロケーションで探されます。

# キーワード引数

  * `arn="arn:aws:braket:us-east-1::device/qpu/quera/Aquila"`: マシンの ARN
  * `region="us-east-1"`: マシンが存在する AWS リージョン
  * `credentials::Union{AWSCredentials, Nothing}=nothing`: ログインするために作成できる `AWS.AWSCredentials` インスタンス。

# ログ/警告/例外

資格情報が無効な場合、`AWS.NoCredentials` 例外がスローされ、`message` 文字列 "Can't find AWS credentials!" が含まれます。

[`BloqadeSchema.hardware_transform`](@ref) は常に呼び出され、`h` の元の波形とハードウェアに互換性のある新しく生成された波形との間の差（エラー）を含むデバッグログも常に出力され、原子位置の同じ変換も含まれます。
