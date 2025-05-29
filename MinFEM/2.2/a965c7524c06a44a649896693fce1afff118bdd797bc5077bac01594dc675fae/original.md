```
integral_over_reference_element(
    f::Function,
    d::Int64;
    order::Int64 = 1
) -> Float64
```

Returns integral of function f over the d-dimensional FEM reference element  computed with Gauss-Legendre quadrature exact at least for polynomials up to given order. 
