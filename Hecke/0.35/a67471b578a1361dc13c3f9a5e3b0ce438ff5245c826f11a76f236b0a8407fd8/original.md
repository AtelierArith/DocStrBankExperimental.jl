```
reduce(A::SMat{T}, g::SRow{T}) -> SRow{T}
```

Given an upper triangular matrix $A$ over a field and a sparse row $g$, this function reduces $g$ modulo $A$.
