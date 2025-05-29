```
KatzRohlf(bandwidth)
```

A [component loss](@ref AbstractComponentLoss) criterion with the loss function

$$
h(\lambda) = 1 - \exp\left(-\left(\frac{\lambda}{b}\right)^2\right),
$$

where $b$ is the *bandwidth* parameter.
