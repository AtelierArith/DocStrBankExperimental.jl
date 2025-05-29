```
hermitian_space(E::NumField, gram::MatElem; cached::Bool = true) -> HermSpace
```

Create the hermitian space over `E` with Gram matrix equals to `gram`. The matrix `gram` must be square and hermitian with respect to the non-trivial automorphism of `E`. The number field `E` must be a quadratic extension, that is, $degree(E) == 2$ must hold.
