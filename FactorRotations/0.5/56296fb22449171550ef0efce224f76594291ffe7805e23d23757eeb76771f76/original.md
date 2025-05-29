```
Concave(bandwidth = 1)
```

The simple concave [component loss](@ref AbstractComponentLoss) factor rotation criterion. It has the loss function

$$
h(\lambda) = 1 - \exp(-\frac{|\lambda|}{b}),
$$

where $b$ is the *bandwidth* parameter.
