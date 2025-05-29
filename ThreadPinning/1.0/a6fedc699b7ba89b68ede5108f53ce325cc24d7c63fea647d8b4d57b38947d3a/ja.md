```
printaffinity(; threadid::Integer = Threads.threadid())
```

Juliaスレッドのアフィニティマスクを印刷します。

キーワード引数 `groupby` を使用して、CPUスレッドの視覚的なグループ化方法を変更できます。デフォルトは `groupby=:socket` です。他の有効な値は `:numa` と `:core` です。
