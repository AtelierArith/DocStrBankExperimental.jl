```
@onthreads threadsel expr
```

`expr`を`threadsel`のスレッドで並列に実行します。

`threadsel`は単一のスレッドIDまたはスレッドIDの範囲（または配列）である必要があります。`threadsel == Base.Threads.threadid()`の場合、`expr`は現在のスレッドで最小限のオーバーヘッドで実行されます。

例 1:

```juliaexpr
tlsum = ThreadLocal(0.0)
data = rand(100)
@onthreads allthreads() begin
    tlsum[] = sum(workpart(data, allthreads(), Base.Threads.threadid()))
end
sum(getallvalues(tlsum)) ≈ sum(data)
```

例 2:

```julia
# 4スレッドを仮定:
tl = ThreadLocal(42)
threadsel = 2:3
@onthreads threadsel begin
    tl[] = Base.Threads.threadid()
end
getallvalues(tl)[threadsel] == [2, 3]
getallvalues(tl)[[1,4]] == [42, 42]
```
