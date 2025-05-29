```
assume_role(principal::AbstractAWSConfig, role; kwargs...) -> AbstractAWSConfig
```

IAM `role`を`principal`エンティティを介して一時的な資格情報で引き受けます。`principal`エンティティは`role`の信頼ポリシーに含まれている必要があります。

[ロールチェイニング](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-role-chaining)は、複数の`assume_role`呼び出しによって手動で指定する必要があります（例："role-a"は"role-b"を引き受ける権限を持っています：`assume_role(assume_role(AWSConfig(), "role-a"), "role-b")`）。

# 引数

  * `principal::AbstractAWSConfig`: `sts:AssumeRole`アクションを実行する主エンティティ（ユーザーまたはロール）のAWS設定と資格情報。
  * `role::AbstractString`: 引き受けるAWS IAMロール。完全なロールARNまたはロール名のみを指定できます。ロール名のみが指定された場合、そのロールは`principal`引数で使用されるのと同じアカウントに存在すると見なされます。

# キーワード

  * `duration::Integer`（オプション）：ロールセッションの持続時間（秒）。
  * `mfa_serial::AbstractString`（オプション）：`AssumeRole` API呼び出しを行うユーザーに関連付けられたMFAデバイスの識別番号。ハードウェアデバイスのシリアル番号（"GAHT12345678"）または仮想デバイスのARN（"arn:aws:iam::123456789012:mfa/user"）のいずれかです。指定された場合、MFAトークンは`token`またはインタラクティブプロンプトを介して提供する必要があります。
  * `token::AbstractString`（オプション）：MFAデバイスによって提供される値。`mfa_serial`が設定されている場合のみ指定できます。
  * `session_name::AbstractString`（オプション）：このAPIリクエストに関連付けられた一意のロールセッション名。
