```
Unitary( U :: AbstractMatrix ) <: Operator{T}
```

Unitary matrices represent the physical evolution of quantum states. The Constructor, `Unitary(U)`, throws a `DomainError` if the provided matrix, `U` is not unitary.
