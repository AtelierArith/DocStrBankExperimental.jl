```
kaplanyorke_dim(λs::AbstractVector)
```

Calculate the Kaplan-Yorke dimension, a.k.a. Lyapunov dimension [Kaplan1979](@cite) from the given Lyapunov exponents `λs`.

## Description

The Kaplan-Yorke dimension is simply the point where `cumsum(λs)` becomes zero (interpolated):

$$
 D_{KY} = k + \frac{\sum_{i=1}^k \lambda_i}{|\lambda_{k+1}|},\quad k = \max_j \left[ \sum_{i=1}^j \lambda_i > 0 \right].
$$

If the sum of the exponents never becomes negative the function will return the length of the input vector.

Useful in combination with `lyapunovspectrum` from ChaosTools.jl.
