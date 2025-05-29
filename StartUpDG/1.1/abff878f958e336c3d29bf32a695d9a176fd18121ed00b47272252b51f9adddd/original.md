```
TensorProductQuadrature{T}
```

A type parameter to `Polynomial` indicating that the quadrature has a tensor  product structure. Example usage: 

```julia
# these are both equivalent
approximation_type = Polynomial{TensorProductQuadrature}(gauss_quad(0, 0, 1)) 
approximation_type = Polynomial(TensorProductQuadrature(gauss_quad(0, 0, 1)))
```
