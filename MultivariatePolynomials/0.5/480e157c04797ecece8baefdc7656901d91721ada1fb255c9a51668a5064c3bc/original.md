```
constant_term(α, p::AbstractPolynomialLike)
```

Creates a constant term with coefficient α and the same variables as p.

```
constant_term(α, ::Type{PT} where {PT<:AbstractPolynomialLike}
```

Creates a constant term of the term type of a polynomial of type `PT`.
