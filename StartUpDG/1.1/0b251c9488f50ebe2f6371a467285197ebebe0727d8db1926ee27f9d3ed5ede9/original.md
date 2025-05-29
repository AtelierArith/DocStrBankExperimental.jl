```
MultidimensionalQuadrature
```

A type parameter for `Polynomial` indicating that the quadrature  has no specific structure. Example usage: 

```julia
# these are both equivalent
approximation_type = Polynomial{MultidimensionalQuadrature}() 
approximation_type = Polynomial(MultidimensionalQuadrature())
```
