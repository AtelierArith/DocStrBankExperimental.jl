```
req_wires(m::MeasurementOperator{M,G})
```

Minimum number of required qubit wires in a circuit to host the measurement operator `m`.

```jldoctest
julia> meas = mop(X, (4,));
julia> req_wires(meas)
4
```
