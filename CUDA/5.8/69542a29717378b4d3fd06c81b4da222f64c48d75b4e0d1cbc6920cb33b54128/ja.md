```
vote_uni_sync(mask::UInt32, predicate::Bool)
```

アクティブなスレッドのすべてに対して `predicate` を評価し、いずれかのスレッドで `predicate` が同じであるかどうかを返します。
