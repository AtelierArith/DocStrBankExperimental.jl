```
point2address(P::Secp256k1.Point, compressed::Bool, testnet::Bool) -> String
```

Secp256k1.Point に基づいて Base58 ビットコインアドレスを返します。圧縮は提供されていない場合は true に設定されます。テストネットはデフォルトで false に設定されています。
