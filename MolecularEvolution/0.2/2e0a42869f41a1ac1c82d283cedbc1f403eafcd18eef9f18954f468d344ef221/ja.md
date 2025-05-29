sample*down!(root::FelNode,models,partition*list)

モデルの下でサンプルを生成します。root.parent*messageは開始分布として使用され、node.messageにはサンプリングされたメッセージが含まれます。modelsは、ツリー上のメッセージが1つのPartitionのみを含む場合は単一のモデル、またはメッセージが>1 Partitionを持つ場合はモデルの配列、またはノードを受け取り、Vector{<:BranchModel}を返す関数である必要があります。partition*list（例：1:3または[1,3,5]）を使用すると、実行するパーティションを選択できます。
