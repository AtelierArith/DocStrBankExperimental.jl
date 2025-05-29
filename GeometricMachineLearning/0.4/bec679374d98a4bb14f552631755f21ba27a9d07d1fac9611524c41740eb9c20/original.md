```
MatrixSoftmax
```

Like [`VectorSoftmax`](@ref) but for matrices:

$$
[\mathrm{softmax}(A)]_{ij} = \frac{e^{A_{ij}}}{\sum_{i'=1, j'=1}^{d,\bar{d}}e^{A_{ij}}}. 
$$
