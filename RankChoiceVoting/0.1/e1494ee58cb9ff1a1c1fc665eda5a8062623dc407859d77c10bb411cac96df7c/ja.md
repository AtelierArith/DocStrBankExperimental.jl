```
satisfies(::Fails, system::VotingSystem, criteria::Monotonicity, rankings::Ranks; n_reps=1000, _...)
```

モンテカルロシミュレーションを使用して、投票システムが単調性基準を満たしているかどうかをテストします。

# 引数

  * `system::VotingSystem`: 投票システムオブジェクト
  * `criteria::Monotonicity`: 単調性基準オブジェクト
  * `rankings::Ranks`: ランクカウントとユニークランクからなるランク選択投票オブジェクト

# キーワード

  * `n_reps=1000`: 違反を検索する際に実行するモンテカルロシミュレーションの最大数
