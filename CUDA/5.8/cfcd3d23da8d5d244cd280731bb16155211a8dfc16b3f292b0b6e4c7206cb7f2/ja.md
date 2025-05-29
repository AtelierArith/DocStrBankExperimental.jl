```
vote_any_sync(mask::UInt32, predicate::Bool)
```

アクティブなスレッドのすべてに対して `predicate` を評価し、いずれかのスレッドで `predicate` が真であるかどうかを返します。
