```
position = ∂2(X)
```

Used by elements' `residual` or `lagrangian` to extract the zero-th order time derivative from the variables `X` and `U`. Where the solver does not provide this derivative (e.g. a static solver), the output is a vector of zeros.

See also: [`∂0`](@ref),[`∂1`](@ref),[`getsomedofs`](@ref)  
