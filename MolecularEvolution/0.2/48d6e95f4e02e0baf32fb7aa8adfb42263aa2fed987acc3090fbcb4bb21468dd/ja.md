```
branchlength_optim!(tree::FelNode, models;  <keyword arguments>)
```

黄金分割探索法、またはオプションでブレント法を使用して、すべてのブランチを再帰的に最適化し、メッセージの整合性を維持します。最初にfelsenstein!()を実行している必要があります。modelsは、ツリーのメッセージが1つのパーティションのみを含む場合は単一のモデル、またはメッセージが>1パーティションを持つ場合はモデルの配列、またはノードを受け取り、異なるブランチごとにモデルを変える必要がある場合はVector{<:BranchModel}を返す関数であることができます。

# キーワード引数

  * `partition_list=nothing`: (例: 1:3または[1,3,5]) 実行するパーティションを選択できます（ただし、すべてのモデルでブランチ長を最適化したいと思うでしょう。デフォルトオプションです）。
  * `tol=1e-5`: `bl_optimizer`の絶対許容誤差。
  * `bl_optimizer::UnivariateModifier=GoldenSectionOpt()`: ブランチ長の対数尤度を最適化するために使用されるアルゴリズム。黄金分割探索法に加えて、`bl_optimizer=BrentsMethodOpt()`を設定することでブレント法を使用できます。
  * `sort_tree=false`: [`lazysort!`](@ref)が実行されるかどうかを決定し、初期化する必要のある一時的なメッセージの量を減らすことができます。
  * `traversal=Iterators.reverse`: トラバーサルを決定する関数で、イテラブルを順列します。
  * `shuffle=false`: ランダムにシャッフルされたトラバーサルを行い、`traversal`をオーバーライドします。
