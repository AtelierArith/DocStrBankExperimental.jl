```
ParallelTuple(xs)
```

Flux.jlモデルで使用するための`Tuple`の薄いラッパーです。

[`ChainTuple`](@ref)、[`ParallelTuple`](@ref)、および[`SkipConnectionTuple`](@ref)を組み合わせることで、データ`xs`を保存し、型の盗用のリスクを冒すことなくFluxモデルの構造を保持できます。
