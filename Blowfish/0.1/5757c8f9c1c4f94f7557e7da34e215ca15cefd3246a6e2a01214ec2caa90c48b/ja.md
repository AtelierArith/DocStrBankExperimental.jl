```
Encrypt!(c::Cipher, dst::Array{UInt8, 1}, src::Array{UInt8, 1})
```

Encryptは、キーkを使用して8バイトのバッファsrcを暗号化し、その結果をdstに格納します。ブロックより大きいデータ量の場合、連続するブロックに対して単にEncryptを呼び出すことは安全ではないことに注意してください。
