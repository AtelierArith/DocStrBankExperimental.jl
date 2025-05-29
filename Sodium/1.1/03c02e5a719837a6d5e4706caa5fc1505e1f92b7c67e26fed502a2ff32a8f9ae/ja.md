```
seal(message::Base.SecretBuffer, publickey)
```

秘密のメッセージを保持する `SecretBuffer` とリモートからの base64 エンコードされた公開鍵を受け取ります。`libsodium.crypto_box_seal` を呼び出すための残りの引数は自動的に推測されます。その後、メッセージは `shred!` され、結果は base64 エンコードされた文字列として返されます。
