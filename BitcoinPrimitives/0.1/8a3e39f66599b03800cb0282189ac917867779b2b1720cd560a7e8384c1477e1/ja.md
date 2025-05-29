```
serialize(program::Witness) -> Vector{UInt8}
```

`Witness`データ型をシリアライズします。最初に`TxIn`のスタックアイテムの数を示す`CompactSizeUInt`が続きます。その後、スタックアイテムが続き、各アイテムは長さを示す`CompactSizeUInt`で始まります。
