```
DensityMatrixSimulator([::T], qubit_count::Int, shots::Int) -> DensityMatrixSimulator{T, Matrix{T}}
```

Create a `DensityMatrixSimulator` with `2^qubit_count x 2^qubit_count` elements and `shots` shots to be measured. The default element type is `ComplexF64`.
