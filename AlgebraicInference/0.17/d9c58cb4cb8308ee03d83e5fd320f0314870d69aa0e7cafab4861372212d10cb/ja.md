```
init(
    problem::InferenceProblem,
    elimination_algorithm::EliminationAlgorithm=MinFill(),
    supernode_type::SupernodeType=Node(),
    architecture_type::ArchitectureType=ShenoyShafer())
```

推論問題のためのソルバーを構築します。これはいくつかのステップを含みます：

```
相互作用グラフ
    ↓ 排除アルゴリズム
排除ツリー
    ↓ スーパー ノードタイプ
結合ツリー
```

まず、排除アルゴリズムを使用してモデルの相互作用グラフから排除ツリーを構築します。次に、排除ツリーのノードがスーパー ノードにマージされ、結合（またはジャンクション）ツリーが形成されます。

[`solve!`](@ref) がソルバーで呼び出されると、メッセージパッシングアルゴリズムが使用されて解が計算されます。
