```
gaussian(σ = 1.0)
```

Returns an in-place real valued mutation function that performs the normal distributed mutation [^1].

The mutation operator randomly chooses a number $z$ in from the normal distribution $\mathcal{N}(0,\sigma)$ with standard deviation $\sigma$. The mutated individual is given by

  * $x_i^\prime = x_i + z_i$
