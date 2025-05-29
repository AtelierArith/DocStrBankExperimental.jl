```
gaussian(x, s::AnisotropicStrategy)
```

Performs Gaussian anisotropic mutation of the recombinant `x` given the strategy `s`  by adding Gaussian noise as follows:

  * $x_i^\prime = x_i + s.\sigma_i \mathcal{N}_i(0,1)$
