```
count_violations(system::VotingSystem, criterion::CondorcetWinner, rankings::Ranks; _...)
```

与えられた投票システムに対するコンドルセの違反の数をカウントします。カウントは0または1です。

# 引数

  * `system::VotingSystem`: 投票システムオブジェクト
  * `criterion::CondorcetWinner`: コンデュルセ基準オブジェクト
  * `rankings::Ranks`: ランクカウントとユニークランクからなるランク選択投票オブジェクト
