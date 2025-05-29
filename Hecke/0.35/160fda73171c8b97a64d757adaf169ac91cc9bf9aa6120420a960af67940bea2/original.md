```
reduce(A::SMat{T}, g::SRow{T}, m::T) -> SRow{T}
```

Given an upper triangular matrix $A$ over the integers, a sparse row $g$ and an integer $m$, this function reduces $g$ modulo $A$ and returns $g$ modulo $m$ with respect to the symmetric residue system.
