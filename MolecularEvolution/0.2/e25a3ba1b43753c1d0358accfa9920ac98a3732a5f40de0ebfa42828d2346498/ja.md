```
log_likelihood!(tree::FelNode, models; partition_list = nothing)
```

最初に上向きフェルステンのパスを再計算し、その後この木の対数尤度を計算します。modelsは、木のメッセージが1つのパーティションしか含まない場合は単一のモデルであるか、メッセージが>1パーティションを持つ場合はモデルの配列であるか、またはノードを受け取り、異なる枝ごとにモデルを変える必要がある場合はVector{<:BranchModel}を返す関数です。partition_list（例：1:3または[1,3,5]）を使用すると、実行するパーティションを選択できます。
