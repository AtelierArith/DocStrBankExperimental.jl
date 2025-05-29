```
FBMKernel(; h::Real=0.5)
```

Fractional Brownian motion kernel with Hurst index `h`.

# Definition

For inputs $x, x' \in \mathbb{R}^d$, the fractional Brownian motion kernel with [Hurst index](https://en.wikipedia.org/wiki/Hurst_exponent#Generalized_exponent) $h \in [0,1]$ is defined as

$$
k(x, x'; h) =  \frac{\|x\|_2^{2h} + \|x'\|_2^{2h} - \|x - x'\|^{2h}}{2}.
$$
