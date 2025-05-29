```
@with_parallelizer(parallelizer, expr)
```

このマクロは、関数呼び出しまたはコードブロックを並列化するために使用できます。このマクロは、関数が並列化可能であることを確認し、その後、指定された `parallelizer` と `expr` を使って `parallelize` を呼び出します。
