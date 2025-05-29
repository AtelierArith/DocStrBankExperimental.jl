```
trapezoidal_epw(k::Int [; rationalize=false [, devisor=false]])
```

Endpoint weights vector $a=[a_1,⋯\ a_k]$ of trapeziodal rule optimized for functions of polynomial form,

$$
    ∫_0^n f(x) dx = a_1 (f_0+f_n) + ⋯ + a_k (f_{k-1}+f_{n-k+1})
                                                         + (f_k+⋯+f_{n-k}),
$$

where $k$ is *odd*. The rule is exact for polynonials of degree $d=0,\ 1, ⋯,\ k-1$. For $k=1$ the rule reduces to the ordinary trapezoidal rule. By default the output is in Float64, optionally the output is rational, with or without specification of the gcd devisor.

#### Example:

```
[trapezoidal_epw(k; rationalize=true, devisor=true) for k=1:2:9]
5-element Vector{Tuple{Int64, Int64, Vector{Int64}}}:
  (1, 2, [1])
  (3, 24, [9, 28, 23])
  (5, 1440, [475, 1902, 1104, 1586, 1413])
  (7, 120960, [36799, 176648, 54851, 177984, 89437, 130936, 119585])
  (9, 7257600, [2082753, 11532470, 261166, 16263486, -1020160, 12489922,
                                                     5095890, 7783754, 7200319])
```
