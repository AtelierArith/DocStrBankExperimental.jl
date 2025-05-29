```
create_decision_model(network::Network, tspan; node_strategy::DataStructures.OrderedDict, species::Type{<:Species}=AedesAegypti,do_binary::Bool=false, optimizer=nothing)
```

数学プログラムを構築します。問題はNLP（do*binary=false）またはMINLP（do*binary=true）として作成されます。
