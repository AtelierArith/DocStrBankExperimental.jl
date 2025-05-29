```
MeasurementOperator{M,G}
```

一般的な測定演算子。`M`は測定演算子によって影響を受けるワイヤの数であり、`G`は実際の演算子のタイプ（ゲートまたはスパース行列）です。

```
julia> m = MeasurementOperator(X, (1,))
MeasurementOperator{1,XGate}(XGate(), (1,))

julia> m = MeasurementOperator([0 1; 1 0], (1,))
MeasurementOperator{1,SparseArrays.SparseMatrixCSC{Complex{Float64},Int64}}(
  [2, 1]  =  1.0+0.0im
  [1, 2]  =  1.0+0.0im, (1,))
```
