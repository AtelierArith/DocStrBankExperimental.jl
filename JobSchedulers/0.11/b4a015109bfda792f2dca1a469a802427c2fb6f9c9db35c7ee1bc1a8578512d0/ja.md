```
Job(p::Program; kwargs...)
Job(p::Program, inputs; kwargs...)
Job(p::Program, inputs, outputs; kwargs...)
```

`Pipelines.jl` パッケージの `Program` を使用して `Job` を作成します。これらの 3 つのメソッドは、`Pipelines.jl` に定義されている `run(::Program, ...)` のラッパーです。

`kwargs...` には `Job(::BaseAbstractCmd, ...)` および `run(::Program, ...)` のキーワード引数が含まれます。

参照: [`run`](@ref)
