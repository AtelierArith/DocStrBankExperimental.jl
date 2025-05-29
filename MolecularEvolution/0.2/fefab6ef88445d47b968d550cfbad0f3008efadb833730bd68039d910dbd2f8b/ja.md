```
cascading_max_state_dict(tree::FelNode, model; partition_list = 1:length(tree.message), node_message_dict = Dict{FelNode,Vector{<:Partition}}())
```

ツリーとモデル（単一のモデル、モデルの配列、または FelNode->Array{<:BranchModel} をマッピングする関数のいずれか）を受け取り、ノードをその推定された祖先にマッピングする辞書を返します。以下のスキームに従います：周辺尤度を最大化する状態がルートで選択され、その後、各ノードについて、親ノードの最大化された状態とすべての子孫の観察に条件付けられた最大尤度状態が選択されます。partition_list によってパーティションのサブセットを指定でき、メモリの再割り当てを避けるために辞書を渡すことができます。これは、何度も実行する場合に便利です。
