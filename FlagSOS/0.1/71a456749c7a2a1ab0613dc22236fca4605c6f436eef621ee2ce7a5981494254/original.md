```
labelCanonically(F::QuantumFlag{T,R})::QuantumFlag{T,R} where {T <: Flag, R <: Real}
```

Labels `F` canonically. If two Flags are isomorphic, this function should return the same Flag.
