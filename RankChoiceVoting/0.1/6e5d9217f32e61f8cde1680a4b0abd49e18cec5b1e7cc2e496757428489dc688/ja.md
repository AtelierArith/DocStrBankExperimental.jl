```
satisfies(system::VotingSystem, criterion::Consistency, rankings::Ranks; n_max=1000, _...)
```

モンテカルロシミュレーションを使用して、投票システムが一貫性基準を満たしているかどうかをテストします。

# 引数

  * `system::VotingSystem`: 投票システムオブジェクト
  * `criterion::Consistency`: 一貫性基準オブジェクト
  * `rankings::Ranks`: ランク数とユニークなランクからなるランク選択投票オブジェクト

# キーワード

  * `n_reps`: 実行する最大モンテカルロシミュレーション数
