```
sync_threads_or(predicate)
```

`sync_threads()` と同じですが、ブロックのすべてのスレッドに対して predicate を評価し、いずれかのスレッドで `predicate` が `true` に評価される場合にのみ `true` を返すという追加機能があります。
