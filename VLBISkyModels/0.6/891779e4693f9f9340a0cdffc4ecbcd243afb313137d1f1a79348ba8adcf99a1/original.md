```
PolExp2Map(a, b, c, d, grid::AbstractRectiGrid)
```

Constructs an polarized intensity map model using the matrix exponential representation from [Arras 2021 (Thesis)](https://www.philipp-arras.de/assets/dissertation.pdf).

Each Stokes parameter is parameterized as

```
I = exp(a)cosh(p)
Q = exp(a)sinh(p)b/p
U = exp(a)sinh(p)c/p
V = exp(a)sinh(p)d/p
```

where `a,b,c,d` are real numbers with no conditions, and `p=√(a² + b² + c²)`.
