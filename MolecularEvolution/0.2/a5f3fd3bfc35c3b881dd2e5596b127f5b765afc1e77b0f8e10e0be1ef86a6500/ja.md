```
felsenstein_roundtrip!(tree::FelNode, models; partition_list = 1:length(tree.message), temp_message = copy_message(tree.message[partition_list]))
```

通常、木の根で呼び出すべきです。まず、Felsensteinパスを先端から根に向かって伝播させ、その後、時間の方向を逆にして（すなわち、forward! = backward!）、根から先端に向かってFelsensteinパスを伝播させます。**これは最適な根を探すときに便利です**（[`root_optim!`](@ref）を参照）。modelsは、木のメッセージが1つのパーティションしか含まれていない場合は単一のモデルであるか、メッセージが>1パーティションを持つ場合はモデルの配列であるか、ノードを受け取り、異なる枝ごとにモデルを変える必要がある場合はVector{<:BranchModel}を返す関数であることができます。partition_list（例：1:3または[1,3,5]）を使用すると、どのパーティションを実行するかを選択できます。
