```
stabilizers(code) -> BitMatrix
```

Return the stabilizers in binary symplectic form.

Each row is a stabilizer generator. An overcomplete set of generators can be included to simplify decoding.

!!! note "Abstract method"
    This method should be implemented for concrete subtypes or duck-typed implementations of [`StabilizerCode`](@ref).

