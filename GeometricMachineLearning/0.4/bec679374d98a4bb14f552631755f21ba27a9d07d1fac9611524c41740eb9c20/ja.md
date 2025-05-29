```
MatrixSoftmax
```

行列に対する[`VectorSoftmax`](@ref)のようなものです：

$$
[\mathrm{softmax}(A)]_{ij} = \frac{e^{A_{ij}}}{\sum_{i'=1, j'=1}^{d,\bar{d}}e^{A_{ij}}}. 
$$
