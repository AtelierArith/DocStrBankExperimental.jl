```
x = TypeFutures(y::T, f[, pids=procs()], fargs...)
```

Construt a `x::TypeFutures` from `y::T` on workers defined by the process id's `pids`.  On each worker `pid`, `f` is evaluated, and a future for what is returned by `f` is stored.

# Example

```
using Distributed
addprocs(2)
@everywhere using DistributedOperations
@everywhere struct MyStruct
    x::Vector{Float64}
    y::Vector{Float64}
end
@everywhere foo() = MyStruct(rand(10), rand(10))
x = foo()
x = TypeFutures(x, foo, procs())
@show remotecall_fetch(localpart, workers()[1], x)
rmprocs(workers())
```
