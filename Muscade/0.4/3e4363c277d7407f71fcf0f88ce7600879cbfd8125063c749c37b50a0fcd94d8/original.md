```
velocity = ∂1(X)
```

Used by elements' `residual` or `lagrangian` to extract the first order time derivative from the variables `X` and `U`. Where the solver does not provide this derivative (e.g. a static solver), the output is a vector of zeros.

See also: [`∂0`](@ref),[`∂2`](@ref),[`getsomedofs`](@ref)  
