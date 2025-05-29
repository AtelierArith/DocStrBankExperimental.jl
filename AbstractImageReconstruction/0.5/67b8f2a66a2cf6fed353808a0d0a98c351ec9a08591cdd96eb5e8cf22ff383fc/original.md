```
process(algo::Union{A, Type{A}}, param::AbstractImageReconstructionParameters, inputs...) where A <: AbstractImageReconstructionAlgorithm
```

Process `inputs` with algorithm `algo` and parameters `param`. Returns the result of the processing step. If not implemented for an instance of `algo`, the default implementation is called with the type of `algo`.
