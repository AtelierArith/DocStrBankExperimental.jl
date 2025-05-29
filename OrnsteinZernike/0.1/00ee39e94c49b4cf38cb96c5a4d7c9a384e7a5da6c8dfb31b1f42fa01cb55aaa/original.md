```
Khanpour <: Closure
```

Implements the Khanpour closure $b(r) = \frac{1}{\alpha}\ln(1+\alpha\gamma(r)) - \gamma  $. Here $\alpha$ is a free parameter that can be determined with thermodynamic consistency.

Example:

```julia
closure = Khanpour(0.5)
```

References:

Khanpour, Mehrdad. "A unified derivation of Percus–Yevick and hyper-netted chain integral equations in liquid state theory." Molecular Physics 120.5 (2022): e2001065.
