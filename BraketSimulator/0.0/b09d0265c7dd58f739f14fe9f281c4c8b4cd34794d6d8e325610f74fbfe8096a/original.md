```
StateVectorSimulator([::T], qubit_count::Int, shots::Int) -> StateVectorSimulator{T, Vector{T}}
```

Create a `StateVectorSimulator` with `2^qubit_count` elements and `shots` shots to be measured. The default element type is `ComplexF64`.
