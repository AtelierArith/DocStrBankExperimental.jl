```
RBFModel( features, labels, φ = Multiquadric(), poly_deg = 1; kwargs ... )
```

Construct a `RBFModel` from the feature vectors in `features` and  the corresponding labels in `lables`, where `φ` is a `RadialFunction` or a vector of  `RadialFunction`s.

Scalar data can be used, it is transformed internally. 

StaticArrays can be used, e.g., `features :: Vector{<:SVector}`.  Providing `SVector`s only might speed up the construction.

If the degree of the polynomial tail, `poly_deg`, is too small it will be set to `cpd_order(φ)-1`.

If the RBF centers do not equal the the `features`, you can use the keyword argument `centers` to pass a list of centers. If `φ` is a vector, then the length of `centers` and `φ` must be equal and  `centers[i]` will be used in conjunction with `φ[i]` to build a `ShiftedKernel`. 

If `features` has 1D data, the output of the model will be a 1D-vector. If it should be a scalar instead, set the keyword argument `vector_output` to `false`.
