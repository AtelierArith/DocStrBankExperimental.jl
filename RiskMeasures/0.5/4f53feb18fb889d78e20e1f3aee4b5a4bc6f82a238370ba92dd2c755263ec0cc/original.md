```
softmin(x̃, β; x̃min check_inputs = true)
```

Compute a weighted softmin function for random variable `x̃` with risk level `β`.  This can be seen as an approximation of the arg min function and not the min function.

The operator computes a distribution p such that

$$
p_i = \frac{e^{-β x_i}}{\mathbb{E}[e^{-β x̃}]}
$$

The optional `x̃min` parameter is used as an offset in order to avoid overflows when computing the exponential function. If not provided, the minimum value of `x̃` is used instead. 

The value β must be positive
