```
ThreadedCPU <: CPU

ThreadedCPU()
```

[`Processor`](@ref) フラグは `Threads.nthreads()` CPU を使用することを指定します。

次のように指定します：

```julia
ruleset = Ruleset(rule; proc=ThreadedCPU())
# または
output = sim!(output, rule; proc=ThreadedCPU())
```
