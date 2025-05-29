```
satisfies(system::VotingSystem, criterion::MutualMajority, rankings::Ranks; _...)
```

投票システムが相互多数基準を満たしているかどうかをテストします。

# 引数

  * `system::VotingSystem`: 投票システムオブジェクト
  * `criterion::MutualMajority`: 多数基準オブジェクト
  * `rankings::Ranks`: ランク数とユニークなランクからなる選択投票オブジェクト
