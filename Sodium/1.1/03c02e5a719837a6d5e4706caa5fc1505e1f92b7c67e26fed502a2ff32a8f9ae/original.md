```
seal(message::Base.SecretBuffer, publickey)
```

Takes a `SecretBuffer` holding a secret message and a base64 encoded public key from the remote. All remaining arguments to call `libsodium.crypto_box_seal` are inferred automatically. After that call, message is `shred!`ed and the result is returned as a base64 encoded string.
