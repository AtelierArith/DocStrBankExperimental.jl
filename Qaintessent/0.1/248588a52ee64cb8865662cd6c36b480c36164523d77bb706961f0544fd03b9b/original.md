```
MeasurementOperator{M,G}
```

General measurement operator. `M` is the number of wires affected by the measurement operator, `G` is the actual operator type (gate or sparse matrix).

```
julia> m = MeasurementOperator(X, (1,))
MeasurementOperator{1,XGate}(XGate(), (1,))

julia> m = MeasurementOperator([0 1; 1 0], (1,))
MeasurementOperator{1,SparseArrays.SparseMatrixCSC{Complex{Float64},Int64}}(
  [2, 1]  =  1.0+0.0im
  [1, 2]  =  1.0+0.0im, (1,))
```
