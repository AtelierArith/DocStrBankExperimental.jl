```
MonteCarloTreeSearch(
	n_rollouts::Int64 = 50,
	max_depth::Int64 = 50,
	heuristic::Heuristic = NullHeuristic(),
	selector::MCTSNodeSelector = BoltzmannUCBSelector(),
	estimator::MCTSLeafEstimator = RandomRolloutEstimator()
end
```

モンテカルロ木探索（`MCTS`の略）[1]を使用するプランナーで、カスタマイズ可能な初期値`heuristic`、ノード`selector`戦略、および葉ノード値`estimator`を持っています。

# 引数

  * `n_rollouts`: 実行する検索ロールアウトの数。
  * `max_depth`: ロールアウトの最大深さ（選択および推定フェーズを含む）。
  * `heuristic`: 新しく遭遇した状態/葉ノードの初期値ヒューリスティック。
  * `selector`: 以前に訪れたノードの選択戦略（例：MaxUCB）。
  * `estimator`: 葉ノード値の推定器（例：ランダムまたはポリシーベースのロールアウト）。
