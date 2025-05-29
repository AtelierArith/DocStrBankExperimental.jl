```
Laplacian(cache::BasicILMCache,coeff_factor::Real[,with_inverse=true])
```

Create an invertible Laplacian operator for the grid in `cache`, using the index or grid scaling associated with `cache`. The operator is pre-multiplied by the factor `coeff_factor`.
