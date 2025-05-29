```
satisfies(system::VotingSystem, criterion::Majority, rankings::Ranks; _...)
```

投票システムが多数決基準を満たすかどうかをテストします。

# 引数

  * `system::VotingSystem`: 投票システムオブジェクト
  * `criterion::Majority`: 多数決基準オブジェクト
  * `rankings::Ranks`: ランク数とユニークなランクから成るランク選択投票オブジェクト
