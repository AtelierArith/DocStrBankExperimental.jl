```
hermitian_space(E::NumField, n::Int; cached::Bool = true) -> HermSpace
```

Create the hermitian space over `E` with dimension `n` and Gram matrix equals to the identity matrix. The number field `E` must be a quadratic extension, that is, $degree(E) == 2$ must hold.
