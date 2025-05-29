```
abstract type Operator{T<:Number} <: AbstractMatrix{Number} end
```

A matrix representing a linear operator that acts upon a complex-valued Hilbert space. The `Operator` is an abstract type that parents all linear operator in quantum mechanics. These matrix types can represent quantum states, evolution, and measurements, each with their individual constraint. These constraints are place upon the children of th `Operator` abstract type.
