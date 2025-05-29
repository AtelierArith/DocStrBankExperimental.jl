```
reset!(stats::GenericExecutionStats)
reset!(stats::GenericExecutionStats, nlp::AbstractNLPModel)
```

`stats`の内部フラグを`false`にリセットして、内容が信頼できないことを示します。`AbstractNLPModel`が提供されている場合、事前に割り当てられたベクトルは問題のサイズに調整されます。
