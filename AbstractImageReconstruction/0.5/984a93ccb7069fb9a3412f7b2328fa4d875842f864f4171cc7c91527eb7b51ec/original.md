```
process(algo::Union{A, Type{A}}, param::AbstractUtilityReconstructionParameters{P}, inputs...) where {A <: AbstractImageReconstructionAlgorithm, P <: AbstractImageReconstructionParameters}
```

Process `inputs` with algorithm `algo` and return the result as if the arguments were given to `P`. Examples of utility `process` are processes which offer caching or remote execution. 
