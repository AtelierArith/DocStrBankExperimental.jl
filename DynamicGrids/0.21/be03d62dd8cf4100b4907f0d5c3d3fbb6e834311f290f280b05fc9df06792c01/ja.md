```
SingleCPU <: CPU

SingleCPU()
```

[`Processor`](@ref) フラグは、単一の CPU 上で単一のスレッドを使用することを指定します。

次のように指定します：

```julia
ruleset = Ruleset(rule; proc=SingleCPU())
# または
output = sim!(output, rule; proc=SingleCPU())
```
