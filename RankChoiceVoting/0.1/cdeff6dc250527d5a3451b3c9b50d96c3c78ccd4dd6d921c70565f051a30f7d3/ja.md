```
count_violations(system::VotingSystem, criterion::CondorcetLoser, rankings::Ranks; _...)
```

与えられた投票システムに対するコンデュルセの敗者基準の違反の数をカウントします。カウントは0または1です。

# 引数

  * `system::VotingSystem`: 投票システムオブジェクト
  * `criterion::CondorcetLoser`: コンデュルセ基準オブジェクト
  * `rankings::Ranks`: ランクカウントとユニークランクからなるランク選択投票オブジェクト
