```
normalization(A::AbstractTensorTrain)
```

Compute the normalization $Z=\sum_{x^1,\ldots,x^L} A^1(x^1)\cdots A^L(x^L)$ and return it as a `Logarithmic`, which stores the sign and the logarithm of the absolute value (see the docs of LogarithmicNumbers.jl https://github.com/cjdoris/LogarithmicNumbers.jl?tab=readme-ov-file#documentation)
