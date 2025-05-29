```
solve(
    problem::InferenceProblem,
    elimination_algorithm::EliminationAlgorithm=MinFill()
    supernode_type::SupernodeType=Node()
    architecture_type::ArchitectureType=ShenoyShafer())
```

推論問題を解決します。これはいくつかのステップを含みます：

```
相互作用グラフ
    ↓ 除去アルゴリズム
除去ツリー
    ↓ スーパー ノードタイプ
結合ツリー
    ↓ アーキテクチャタイプ
解
```

まず、除去アルゴリズムを使用してモデルの相互作用グラフから除去ツリーを構築します。次に、除去ツリーのノードがスーパー ノードに統合され、結合（またはジャンクション）ツリーが形成されます。最後に、メッセージパッシングアルゴリズムを使用して解を計算します。
