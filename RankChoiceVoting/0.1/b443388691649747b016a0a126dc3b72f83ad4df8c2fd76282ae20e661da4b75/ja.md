```
count_violations(system::VotingSystem, criterion::MutualMajority, rankings::Ranks; _...)
```

与えられた投票システムに対する多数派基準の違反の数をカウントします。カウントは0または1です。

# 引数

  * `system::VotingSystem`: 投票システムオブジェクト
  * `criterion::Majority`: 多数派基準オブジェクト
  * `rankings::Ranks`: ランクカウントとユニークランクからなるランク選択投票オブジェクト
