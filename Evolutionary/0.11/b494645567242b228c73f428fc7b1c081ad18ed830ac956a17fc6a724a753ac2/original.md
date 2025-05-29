```
gaussian(s::IsotropicStrategy)
```

Performs in-place mutation of the isotropic strategy `s` modifying its mutated strategy parameter $\sigma$ with Gaussian noise as follows:

  * $\sigma^\prime = \sigma \exp(\tau_0 \mathcal{N}(0,1))$
