```
count_violations(system::VotingSystem, criteria::Monotonicity, rankings::Ranks; n_reps=1000, _...)
```

モンテカルロシミュレーションを使用して、特定の投票システムに対する単調性基準の違反の数をカウントします。

# 引数

  * `system::VotingSystem`: 投票システムオブジェクト
  * `criteria::Monotonicity`: コンデュルセ基準オブジェクト
  * `rankings::Ranks`: ランクカウントとユニークランクからなるランク選択投票オブジェクト

# キーワード

  * `n_reps=1000`: 実行するモンテカルロシミュレーションの最大数
