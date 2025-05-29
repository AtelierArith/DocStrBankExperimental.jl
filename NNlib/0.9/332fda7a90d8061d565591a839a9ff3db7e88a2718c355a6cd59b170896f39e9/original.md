```
gelu_erf(x) = xΦ(x) = 0.5x * (1 + erf(x/√2))
```

Activation function from ["Gaussian Error Linear Units"](https://arxiv.org/abs/1606.08415) without approximation. The SpecialFunctions.jl package needs to be loaded to use this function.
