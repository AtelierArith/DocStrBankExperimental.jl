```
outer(a,b)
a ⊗ b
```

Outer product (or tensor-product) of two `Number`s and/or `MultiValue`s, that is `(a⊗b)[i₁,...,iₙ,j₁,...,jₙ] = a[i₁,...,iₙ]*b[j₁,...,jₙ]`. This falls back to standard multiplication if `a` or `b` is a scalar.
