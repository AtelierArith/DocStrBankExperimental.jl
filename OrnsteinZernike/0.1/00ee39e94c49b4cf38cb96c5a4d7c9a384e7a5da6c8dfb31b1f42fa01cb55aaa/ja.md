```
Khanpour <: Closure
```

Khanpourクロージャを実装します $b(r) = \frac{1}{\alpha}\ln(1+\alpha\gamma(r)) - \gamma $。ここで、$\alpha:は熱力学的一貫性に基づいて決定できる自由パラメータです。

例:

```julia
closure = Khanpour(0.5)
```

参考文献:

Khanpour, Mehrdad. "A unified derivation of Percus–Yevick and hyper-netted chain integral equations in liquid state theory." Molecular Physics 120.5 (2022): e2001065.
