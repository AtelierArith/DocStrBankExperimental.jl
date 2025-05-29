```
gaussian(s::AnisotropicStrategy)
```

Performs in-place mutation of the anisotropic strategy `s` modifying its mutated strategy parameter $\sigma$ with Gaussian noise as follows:

  * $\sigma_i^\prime = \sigma_i \exp(\tau_0 \mathcal{N}(0,1) + \tau_i \mathcal{N}(0,1))$
