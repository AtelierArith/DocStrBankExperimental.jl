```
VectorSoftmax <: AbstractSoftmax
```

Turn an arbitrary vector into a probability vector with:

$$
[\mathrm{softmax}(a)]_i = \frac{e^{a_i}}{\sum_{i'=1}^de^{a_i}}. 
$$

This is what is most often understood under the name "softmax". [`MatrixSoftmax`](@ref) is the matrix version.
