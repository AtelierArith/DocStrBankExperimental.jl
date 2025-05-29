```
x = TypeFutures(T, f, pids, fargs...)
```

プロセスID `pids` で定義されたワーカー上に型 `T` の `x::TypeFutures` を構築します。各ワーカー `pid` で `f` が評価され、`f` によって返されるものの未来が保存されます。

# 例

```
using Distributed
addprocs(2)
@everywhere using DistributedOperations
@everywhere struct MyStruct
    x::Vector{Float64}
    y::Vector{Float64}
end
@everywhere foo() = MyStruct(rand(10), rand(10))
x = TypeFutures(MyStruct, foo, procs())
@show remotecall_fetch(localpart, workers()[1], x)
rmprocs(workers())
```
