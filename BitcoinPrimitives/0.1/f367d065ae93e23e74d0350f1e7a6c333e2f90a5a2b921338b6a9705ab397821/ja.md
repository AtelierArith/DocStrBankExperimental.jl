```
ヘッダー
```

ビットコインブロックチェーンのブロックのヘッダーを表すデータ構造。

データは、実際に解析することなく `NTuple{80, UInt8}` として保存されます。`Header` の要素には `header.element` でアクセスできます。

```julia
header.version
header.prevhash
header.merkleroot
header.time
header.bits
header.nonce
```
