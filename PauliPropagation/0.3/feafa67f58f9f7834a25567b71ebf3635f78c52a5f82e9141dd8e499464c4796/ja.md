```
CliffordGate(symbol::Symbol, qinds::Vector{Int})
CliffordGate(symbol::Symbol, qinds::Int)
```

名前 `symbol` のクリフォードゲートが量子ビット `qinds` に作用します。`symbol` はグローバル `clifford_map` に実装されているクリフォードゲートのいずれかと一致する必要があります。`qinds` は単一の整数、整数のベクトル、または `vec(collect(qinds))` を介してベクトルに変換されるもののいずれかであることができます。
