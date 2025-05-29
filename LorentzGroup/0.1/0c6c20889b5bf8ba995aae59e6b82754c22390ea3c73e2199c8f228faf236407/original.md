```
LorIdentity{T} <: Lorentz{T}
```

The identity element of the Lorentz group, as a matrix containing no run-time data.  Most operations with this object are more efficient than the equivalent with a materialized `SMatrix{4,4}`. The purpose of this object is primarily as a placeholder in generic code.
