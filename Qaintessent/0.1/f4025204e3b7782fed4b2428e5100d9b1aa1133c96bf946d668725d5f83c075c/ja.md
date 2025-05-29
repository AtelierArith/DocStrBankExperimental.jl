```
req_wires(m::MeasurementOperator{M,G})
```

測定演算子 `m` をホストする回路に必要な最小限の量子ビットワイヤの数。

```jldoctest
julia> meas = mop(X, (4,));
julia> req_wires(meas)
4
```
