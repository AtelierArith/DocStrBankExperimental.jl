```
satisfies(system::VotingSystem, criterion::CondorcetLoser, rankings::Ranks; _...)
```

投票システムがコンデュルセの敗者基準を満たしているかどうかをテストします。

# 引数

  * `system::VotingSystem`: 投票システムオブジェクト
  * `criterion::CondorcetLoser`: コンデュルセの敗者基準オブジェクト
  * `rankings::Ranks`: ランク数とユニークなランクからなるランク選択投票オブジェクト
