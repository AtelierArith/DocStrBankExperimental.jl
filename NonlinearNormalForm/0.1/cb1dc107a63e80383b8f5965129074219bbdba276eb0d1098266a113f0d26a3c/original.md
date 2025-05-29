```
mul!(Q::Quaternion, Q1::Quaternion, Q2::Quaternion)
```

Sets `Q` equal to `Q1*Q2`, with zero allocations. `Q` must not be  aliased with either `Q1` or `Q2`.
