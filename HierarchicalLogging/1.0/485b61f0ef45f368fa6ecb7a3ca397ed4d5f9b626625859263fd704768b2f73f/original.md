```
HierarchicalLogger{T<:AbstractLogger} <: AbstractLogger
```

An `AbstractLogger` consisting of one or more child loggers of type `T` with associated names of the form

```julia
    key₁.key₂.key₃. ... .keyₙ
```

Given `H::HierarchicalLogger`, the parent of logger `L` with label `key₁.key₂. ... .keyⱼ` is the logger `P ∈ H` sharing the longest prefix with `L`, i.e., the label for `P` is `key₁.key₂. ... .keyᵢ` for `i < j` maximal in `H`. 

This collection always contains a logger at the root with an empty label. 
