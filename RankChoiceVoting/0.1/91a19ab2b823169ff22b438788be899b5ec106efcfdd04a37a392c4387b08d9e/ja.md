```
count_violations(system::VotingSystem, criterion::ReversalSymmetry, rankings::Ranks; _...)
```

与えられた投票システムに対する反転対称性基準の違反の数をカウントします。違反の数は0または1です。

# 引数

  * `system::VotingSystem`: 投票システムオブジェクト
  * `criterion::ReversalSymmetry`: 反転対称性基準オブジェクト
  * `rankings::Ranks`: ランクカウントとユニークランクからなるランク選択投票オブジェクト
