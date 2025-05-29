```
PolyaGammaPSWSampler(b::Int, z::Real)
```

PSW sampler ([1]) for a Polya-Gamma distribution with parameters `b` and `z`, and Laplace transform

$$
\mathcal{L}(t) = \cosh^b(z) \cosh^{-b}(\sqrt{2t + z^2})
$$

References

  * [1] [https://doi.org/10.1080/01621459.2013.829001](https://doi.org/10.1080/01621459.2013.829001)
