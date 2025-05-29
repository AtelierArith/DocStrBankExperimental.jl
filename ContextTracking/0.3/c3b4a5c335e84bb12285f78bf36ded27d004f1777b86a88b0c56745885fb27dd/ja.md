```
context([id::UInt], [container])
```

新しいコンテキストオブジェクトを取得します。 `id` が渡されない場合、現在のスレッド/タスクのためのグローバルコンテキストを返します。 `container` は `push!`、`getindex`、`empty!`、および `length` 関数をサポートするオブジェクトでなければなりません。 デフォルトは `Dict{Any,Any}` です。
