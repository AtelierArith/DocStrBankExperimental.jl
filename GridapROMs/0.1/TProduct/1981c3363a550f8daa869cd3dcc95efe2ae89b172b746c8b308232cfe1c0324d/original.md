```
TProductDiscreteModel{D,A,B} <: DiscreteModel{D,D} end
```

Tensor product discrete model, storing a vector of 1-D models `models_1d` of length D, and the D-dimensional model `model` defined as their tensor product.
