```
QobjEvo(data::AbstractSciMLOperator; type = Operator(), dims = nothing)
QuantumObjectEvolution(data::AbstractSciMLOperator; type = Operator(), dims = nothing)
```

Generate a [`QuantumObjectEvolution`](@ref) object from a [`SciMLOperator`](https://github.com/SciML/SciMLOperators.jl), in the same way as [`QuantumObject`](@ref) for `AbstractArray` inputs.

Note that `QobjEvo` is a synonym of `QuantumObjectEvolution`
