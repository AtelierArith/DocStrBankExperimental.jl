```
felsenstein!(node::FelNode, models; partition_list = nothing)
```

通常、木の根で呼び出されるべきです。Felsensteinパスを先端から根に向かって伝播させます。modelsは、木のメッセージが1つのPartitionしか含まない場合は単一のモデル、またはメッセージが>1 Partitionを持つ場合はモデルの配列、またはノードを受け取り、異なる枝ごとにモデルを変える必要がある場合はVector{<:BranchModel}を返す関数である可能性があります。partition_list（例：1:3または[1,3,5]）を使用すると、実行するパーティションを選択できます。
