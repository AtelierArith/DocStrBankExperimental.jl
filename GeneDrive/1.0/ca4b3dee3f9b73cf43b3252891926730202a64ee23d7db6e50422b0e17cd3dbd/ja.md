```
create_decision_model(node::Node, tspan; node_strategy::DataStructures.OrderedDict, species::Type{<:Species}=AedesAegypti,do_binary::Bool=false, optimizer=nothing)
```

数学プログラムを構築します。問題はNLP（do*binary=false）またはMINLP（do*binary=true）として作成されます。注意：`Node`は内部的に`Network`オブジェクトとして再作成されます。これは問題を変更するものではありませんが、フォーマットされた結果にインデックス層を追加するため、データ探索に関連しています。
