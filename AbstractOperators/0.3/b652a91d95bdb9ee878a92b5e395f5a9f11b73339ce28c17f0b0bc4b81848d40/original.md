`SoftMax([domainType=Float64::Type,] dim_in::Tuple)`

Creates the softmax non-linear operator with input dimensions `dim_in`.

$$
\sigma(\mathbf{x}) = \frac{e^{\mathbf{x} }}{ \sum e^{\mathbf{x} } }
$$
