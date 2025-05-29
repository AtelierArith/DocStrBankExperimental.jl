```
fudge_inv(s::AbstractStateSpace, ε = 0.001)
```

Allow inverting a proper statespace system by adding a tiny (ε) feedthrough term to the `D` matrix. The system must still be square.
