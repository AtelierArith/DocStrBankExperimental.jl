```
Email
```

メタデータと添付ファイルを含むメール構造。

## フィールド

  * `from::Union{Nothing,Vector{String}}`: メール送信者のアドレスのベクター。
  * `to::Union{Nothing,Vector{String}}`: メール受信者のアドレスのベクター。
  * `date::Union{Nothing,DateTime}`: メールが送信された日時。
  * `text_body::Vector{UInt8}`: メールのテキスト本文のバイナリデータ。
  * `attachments::Vector{EmailAttachment}`: メタデータを含むメールの添付ファイルのベクター。
