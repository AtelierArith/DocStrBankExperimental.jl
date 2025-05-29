```
gaussian(x, s::IsotropicStrategy)
```

Performs Gaussian isotropic mutation of the recombinant `x` given the strategy `s`  by adding Gaussian noise as follows:

  * $x_i^\prime = x_i + s.\sigma \mathcal{N}_i(0,1)$
