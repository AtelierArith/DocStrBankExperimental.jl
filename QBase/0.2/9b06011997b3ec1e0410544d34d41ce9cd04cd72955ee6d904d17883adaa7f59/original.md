```
POVM( Π :: Vector{POVMel{T}} ) <: Measurement{T}
POVM( Π :: Vector{Matrix{T}} ) <: Measurement{T}
```

Positve-operator valued measures (POVMs) represent a general quantum measurement. Each POVM-element is a hermitian, positive-semidefinite matrix. The sum of all POVM-elements yields the identity matrix. The constructor, `POVM(Π)` throws a `DomainError` if the provided array of matrices, `Π` is not a valid POVM.
