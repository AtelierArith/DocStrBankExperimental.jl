```
count_violations(system::VotingSystem, criterion::Majority, rankings::Ranks; _...)
```

与えられた投票システムに対する多数決基準の違反の数をカウントします。

# 引数

  * `system::VotingSystem`: 投票システムオブジェクト
  * `criterion::Majority`: 多数決基準オブジェクト
  * `rankings::Ranks`: ランクカウントとユニークランクから成るランク選択投票オブジェクト
