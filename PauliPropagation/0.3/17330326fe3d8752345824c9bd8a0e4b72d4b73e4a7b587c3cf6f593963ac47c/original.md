```
add!(psum::PauliSum{TermType, CoeffType}, pstr::TermType, coeff::CoeffType)
```

Add a Pauli string `pstr` with coefficient `coeff` to a `PauliSum` `psum`. This changes `psum` in-place. `pstr` needs to have the same type as `paulitype(psum)`, and `coeff` needs to have the same type as `coefftype(psum)`.
