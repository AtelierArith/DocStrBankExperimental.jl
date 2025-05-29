```
Dirac(x)
```

A *Dirac distribution* is parameterized by its only value `x`, and takes its value with probability 1.

$$
P(X = \hat{x}) = \begin{cases}
1 & \quad \text{for } \hat{x} = x, \\
0 & \quad \text{for } \hat{x} \neq x.
\end{cases}
$$

```julia
Dirac(2.5)   # Dirac distribution with value x = 2.5
```

External links:

  * [Dirac measure on Wikipedia](http://en.wikipedia.org/wiki/Dirac_measure)
