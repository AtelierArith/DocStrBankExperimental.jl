```
SeparableSum(f_1, ..., f_k)
```

Given functions `f_1` to `f_k`, return their separable sum, that is

$$
g(x_1, ..., x_k) = \sum_{i=1}^k f_i(x_i).
$$

The object `g` constructed in this way can be evaluated at `Tuple`s of length `k`. Likewise, the `prox` and `prox!` methods for `g` operate with (input and output) `Tuple`s of length `k`.

Example:

```
f = SeparableSum(NormL1(), NuclearNorm()); # separable sum of two functions
x = randn(10); # some random vector
Y = randn(20, 30); # some random matrix
f_xY = f((x, Y)); # evaluates f at (x, Y)
(u, V), f_uV = prox(f, (x, Y), 1.3); # computes prox at (x, Y)
```
