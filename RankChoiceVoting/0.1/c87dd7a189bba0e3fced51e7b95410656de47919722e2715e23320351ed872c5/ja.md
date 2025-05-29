```
satisfies(system::VotingSystem, criterion::CondorcetWinner, rankings::Ranks; _...)
```

投票システムがコンデュルセ勝者基準を満たすかどうかをテストします。

# 引数

  * `system::VotingSystem`: 投票システムオブジェクト
  * `criterion::CondorcetWinner`: コンデュルセ基準オブジェクト
  * `rankings::Ranks`: ランクカウントとユニークランクからなるランク選択投票オブジェクト
