```
support(F::Vector{<:MP.AbstractPolynomialLike}, vars=MP.variables(F), T::Type{<:Integer}=Int32)
```

Compute the support of the polynomial system `F` with the given variables `vars`. The returned matrices have element type `T`.
