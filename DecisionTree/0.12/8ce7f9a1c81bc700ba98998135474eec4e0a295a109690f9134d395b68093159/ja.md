```
prune_tree(tree::Union{Root, LeafOrNode}, purity_thresh=1.0, loss::Function)
```

`tree`を各ノードの予測精度に基づいて剪定します。ここで`tree`は、例えば[`build_tree`](@ref)によって返される任意の`DecisionTree.Root`、`DecisionTree.Node`、または`DecisionTree.Leaf`インスタンスです。

  * `purity_thresh`: スタンプの予測精度がこの値より大きい場合、そのノードは剪定されて葉になります。
  * `loss`: ノードの不純度を計算するための損失関数。利用可能な関数には`DecisionTree.util.entropy`、`DecisionTree.util.gini`、および`DecisionTree.mean_squared_error`が含まれます。分類木と回帰木にはそれぞれデフォルトで`entropy`と`mean_squared_error`が使用されます。木が`Root`でない場合、この引数は結果に影響しません。

`Root`型の木の場合、ノードのいずれかが剪定されると、`featim`フィールドはそのノードの不純度の減少を再計算し、トレーニング観測の総数で割った値を引くことによって更新されます。不純度の減少の計算は、引数`loss`として提供された損失関数を用いて計算されたノードの不純度に基づいています。アルゴリズムは[`impurity_importance`](@ref)ドキュメントに記載されているものと同じです。

この関数は、剪定できるスタンプがなくなるまで再帰します。

!!! warning
    回帰木の場合、精度に基づいて木を剪定することは適切な方法ではないかもしれません。


他にも[`build_tree`](@ref)を参照してください。
