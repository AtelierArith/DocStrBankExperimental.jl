```
Polynomial{T}
```

Represents polynomial approximation types (as opposed to finite differences).  By default, `Polynomial()` constructs a `Polynomial{StartUpDG.DefaultPolynomialType}`. Specifying a type parameters allows for dispatch on additional structure within a polynomial approximation (e.g., collocation, tensor product quadrature, etc). 
