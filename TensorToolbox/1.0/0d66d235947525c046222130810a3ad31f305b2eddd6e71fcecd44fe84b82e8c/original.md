```
TTrank(X::TTtensor,full=false)
TTrank(X::CoreCell,full=false)
```

Representational TT-rank of X. If cores of X are of size R{n-1} x In x Rn, returns (R1,...,R{n-1}) for full=false or (1,R1,....,Rn) for full=true.
