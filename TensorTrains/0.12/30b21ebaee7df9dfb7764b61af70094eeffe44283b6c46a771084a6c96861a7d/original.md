```
LinearAlgebra.normalize!(A::AbstractTensorTrain)
```

Compute the normalization of $Z=\sum_{x^1,\ldots,x^L} A^1(x^1)\cdots A^L(x^L)$ (see [`normalization`](@ref)) and rescale the tensors in `A` such that, after this call, $|Z|=1$. Return the natural logarithm of the absolute normalization $\log|Z|$
