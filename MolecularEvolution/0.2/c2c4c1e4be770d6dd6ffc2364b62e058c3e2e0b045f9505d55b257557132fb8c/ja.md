```
endpoint_conditioned_sample_state_dict(tree::FelNode, model; partition_list = 1:length(tree.message), node_message_dict = Dict{FelNode,Vector{<:Partition}}())
```

ツリーとモデル（単一のモデル、モデルの配列、または FelNode->Array{<:BranchModel} にマッピングする関数のいずれか）を受け取り、葉の観察に基づいてモデル条件下でサンプルを引き出します。これらのサンプルは node*message*dict に保存され、返されます。partition_list によってパーティションのサブセットを指定でき、メモリの再割り当てを避けるために辞書を渡すことができます。これは何度も実行する場合に便利です。
