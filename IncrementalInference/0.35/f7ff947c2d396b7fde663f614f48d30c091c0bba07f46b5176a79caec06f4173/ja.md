```julia
attemptTreeSimilarClique(othertree, seeksSimilar)

```

`othertree::AbstractBayesTree`の内容に基づいて、`seeksSimilar::BayesTreeNodeData`で成功裏に特定された場合にクリークデータを返そうとする特別な内部関数です。

ノート

  * 類似したクリークを特定してスキップするために使用されます（すなわち、計算を再利用します）
