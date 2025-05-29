```
Linear{T,R} <: AbstractLinear{T,R}

Linear{T,R}(itr)
```

Construct a linear combination of type `Linear` with term type `T` and coefficient type `R` out of the term-coefficient pairs provided by the iterator `itr`.

Linear combinations of this type are sparse in the sense that terms and (non-zero) coefficients are internally stored in a dictionary.

Other ways to use this constructor are discussed under `AbstractLinear`.

See also [`AbstractLinear`](@ref), [`DenseLinear`](@ref), [`Linear1`](@ref).
