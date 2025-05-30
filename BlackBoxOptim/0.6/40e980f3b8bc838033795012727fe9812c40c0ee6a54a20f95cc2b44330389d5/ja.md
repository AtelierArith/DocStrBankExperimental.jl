```
update_fitness!([f], eval::Evaluator, candidates; force::Bool=false)
```

`candidates`のフィットネスを計算し、オプションで処理された各候補に`f`を適用します。`force`は、既に存在する非NAフィットネスを再評価するかどうかを指定します。
