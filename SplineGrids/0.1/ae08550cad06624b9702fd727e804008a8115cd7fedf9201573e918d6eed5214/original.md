```
KnotVector(
    n_basis_functions::Integer, 
    degree::Integer; 
    extent::Tuple{Number, Number} = (0,1), 
    distribution::Symbol = :equispaced)
```

Construct a clamped knot vector, i.e. the multiplicity of the first and last knot is degree + 1 and the other multiplicities are 1.

## Arguments

  * `n_basis_functions`: The number of basis functions that will be defined on this knot vector
  * `degree`: The degree of the basis functions that will be defined on this knot vector

## Keyword Arguments

  * `extent`: A tuple (t*min, t*max) defining the extend of the knot vector
  * `distribution`: The distribution of the internal knots. The options are :equispaced or :random
  * `backend`: The KernelAbstractions backend of the arrays in the object. Defaults to `CPU()`.
  * `float_type`: The type of all floating point arrays. Defaults to `Float32`.
  * `int_type`: The type of all integer arrays. Defaults to `Int32`.
