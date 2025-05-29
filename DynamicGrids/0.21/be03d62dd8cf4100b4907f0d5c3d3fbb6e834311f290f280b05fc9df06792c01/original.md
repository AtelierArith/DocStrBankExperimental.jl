```
SingleCPU <: CPU

SingleCPU()
```

[`Processor`](@ref) flag that specifies to use a single thread on a single CPU.

Specifiy with:

```julia
ruleset = Ruleset(rule; proc=SingleCPU())
# or
output = sim!(output, rule; proc=SingleCPU())
```
