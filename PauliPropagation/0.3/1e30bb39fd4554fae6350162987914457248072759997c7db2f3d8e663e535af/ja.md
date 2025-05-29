```
TransferMapGate(transfer_map::Vector{Vector{Tuple{TermType,CoeffType}}}, qinds::Vector{Int})
```

`qinds`に作用する転送マップによって定義された非パラメータ化`StaticGate`。転送マップは手動で構築することも、`totransfermap()`を介して生成することもできます。
