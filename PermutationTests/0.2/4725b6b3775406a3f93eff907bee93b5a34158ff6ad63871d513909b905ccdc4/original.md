```julia
flip(x::Bool)

flip(x::Union{R, I}) where {R<:Real, I<:Int}
```

Invert the sign of a real number or integer and negate a boolean. 

This function may be needed for argument `fstat` to call [`_permTest!`](@ref) or [`_permMcTest!`](@ref) if you  [create your own test](@ref "Create your own test") - see the example on how to create a test for the [Chatterjee correlation](@ref "Example 5: univariate Chatterjee correlation").

It can also be useful when you create a new test in the code you deveolop for computing your own test statistics. 
