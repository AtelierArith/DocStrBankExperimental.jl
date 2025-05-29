```
vote_ballot_sync(mask::UInt32, predicate::Bool)
```

アクティブなスレッドのすべてに対して `predicate` を評価し、N番目のスレッドがアクティブであり、かつ `predicate` が真である場合にのみN番目のビットがセットされた整数を返します。
