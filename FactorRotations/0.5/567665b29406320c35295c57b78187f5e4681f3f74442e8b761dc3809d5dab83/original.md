```
criterion(method::RotationMethod, Λ::Abstractmatrix{<:Real})
```

Calculate the criterion of a given `method` with respect to the factor loading matrix `Λ`.

The method is just a wrapper for a [`criterion_and_gradient!(nothing, method, Λ)`](@ref criterion_and_gradient!) call.
