```
struct INTTPlan{T<:Union{Int32, Int64, UInt32, UInt64}}
```

Struct containing all information necessary to perform a NTT. Either construct directly through `INTTPlan(n, p, npru)`, or see `plan_ntt()`
