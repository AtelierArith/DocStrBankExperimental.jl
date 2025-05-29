```
sync_threads_count(predicate)
```

`sync_threads()` と同じですが、ブロック内のすべてのスレッドに対して述語を評価し、`predicate` が true と評価されるスレッドの数を返すという追加機能があります。
