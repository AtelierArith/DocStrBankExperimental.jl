```
RefElemData(elem::Union{Line, Quad, Hex}, approximation_type::Polynomial{Gauss}, N)
```

Builds a `rd::RefElemData` with (N+1)-point Gauss quadrature in each dimension. 
