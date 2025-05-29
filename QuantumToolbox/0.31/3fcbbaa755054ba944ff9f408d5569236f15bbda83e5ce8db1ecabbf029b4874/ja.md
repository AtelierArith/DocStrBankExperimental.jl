```
QobjEvo(data::AbstractSciMLOperator; type = Operator(), dims = nothing)
QuantumObjectEvolution(data::AbstractSciMLOperator; type = Operator(), dims = nothing)
```

[`QuantumObjectEvolution`](@ref) オブジェクトを [`SciMLOperator`](https://github.com/SciML/SciMLOperators.jl) から生成します。これは、`AbstractArray` 入力に対する [`QuantumObject`](@ref) と同様です。

`QobjEvo` は `QuantumObjectEvolution` の同義語であることに注意してください。
