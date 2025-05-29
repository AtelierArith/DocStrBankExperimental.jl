```
serialize(tx::Tx; force_legacy::Bool=false) -> Vector{UInt8}
```

トランザクションのバイトシリアル化を返します。force_legacyはオプションでtrueに設定でき、SegWit（BIP 141）のトランザクションをレガシートランザクションのようにシリアル化して、適切なtxid計算を可能にします。
