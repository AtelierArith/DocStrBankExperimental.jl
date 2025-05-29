```
marginal_state_dict(tree::FelNode, model; partition_list = 1:length(tree.message), node_message_dict = Dict{FelNode,Vector{<:Partition}}())
```

ツリーとモデル（単一のモデル、モデルの配列、または FelNode->Array{<:BranchModel} にマッピングする関数のいずれか）を受け取り、ノードをその周辺再構成（すなわち P(state|all observations,model)）にマッピングする辞書を返します。partition_list によってパーティションのサブセットを指定でき、メモリの再割り当てを避けるために辞書を渡すことができます。これは、何度も実行する場合に便利です。
