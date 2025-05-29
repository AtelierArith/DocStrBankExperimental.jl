```
uploadtransfer(client::PCloudClient; kwargs...)
```

ファイルを転送し、受信者のメールに転送リンクを作成して送信します。

出典: https://docs.pcloud.com/methods/transfer/uploadtransfer.html

# 引数

  * `sendermail::String`: 送信者のメール
  * `receivermails::String`: 受信者のメール（最大20件）、カンマで区切る

# オプション引数

  * `message::String`: 受信者へのコメントとして機能する短いメッセージ（最大160文字）
  * `progresshash::String`: 転送進捗を観察するために使用されるハッシュ

# 出力例

```
{
    result: 0
}
```
