```
iscommuting(A::MeasurementOperator{L,G}, B::MeasurementOperator{M,H}) where {L,M,G,H}
```

は、[`MeasurementOperator`](@ref) `A` と `B` が可換である場合に true を返します。
