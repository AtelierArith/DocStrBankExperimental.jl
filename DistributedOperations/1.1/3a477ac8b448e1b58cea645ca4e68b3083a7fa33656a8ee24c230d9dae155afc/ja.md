```
x = ArrayFutures(x::Array[, pids=procs()])
```

`x::TypeFutures`を作成し、`myid()`が`x`に割り当てられ、他のすべてのプロセスが`zeros(eltype(x), size(x))`に割り当てられます。
