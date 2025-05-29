```
vote_all_sync(mask::UInt32, predicate::Bool)
```

アクティブなスレッドのすべてに対して `predicate` を評価し、すべてのスレッドに対して `predicate` が真であるかどうかを返します。
