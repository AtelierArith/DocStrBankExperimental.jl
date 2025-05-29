```
exchange!(rcv,snd,graph::ExchangeGraph) -> Task
```

[`exchange`](@ref) のインプレースおよび擬似非同期バージョンです。この関数は即座に戻り、更新された値を持つ `rcv` を生成するタスクを返します。更新されたバージョンの `rcv` を取得するには `fetch` を使用してください。入力 `rcv` は [`allocate*exchange`](@ref) を使用して割り当てることができます。
