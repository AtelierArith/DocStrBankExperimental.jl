```
felsenstein_down!(node::FelNode, models; partition_list = 1:length(tree.message), temp_message = copy_message(tree.message))
```

通常、木の根で呼び出すべきです。Felsensteinパスを根から先端まで伝播させます。通常、最初にfelsenstein!()を呼び出すべきです。modelsは、木のメッセージが1つのパーティションしか含まない場合は単一のモデルであるか、メッセージが>1パーティションを持つ場合はモデルの配列であるか、またはノードを受け取り、異なる枝ごとにモデルを変える必要がある場合はVector{<:BranchModel}を返す関数であることができます。partition_list（例：1:3または[1,3,5]）を使用すると、実行するパーティションを選択できます。
