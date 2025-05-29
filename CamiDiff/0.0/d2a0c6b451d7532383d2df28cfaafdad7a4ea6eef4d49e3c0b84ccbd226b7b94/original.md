```
trapezoidal_integration(f, x1, x2, weights)
```

Integral of the tabulated function $f=[f_0,⋯\ f_n]$ over the `domain` $x1 ≤ x ≤ x2$ using the optimized trapezoidal rule with endpoint correction by the weights vector `weights`,

$$
    ∫_0^n f(x) dx = a_1 (f_0+f_n) + ⋯ + a_k (f_{k-1}+f_{n-k+1})
                                                         + (f_k+⋯+f_{n-k}).
$$

The rule is exact for polynonials of degree $d=0,\ 1,⋯\ k-1$. For $k=1$ the rule reduces to the ordinary trapezoidal rule (weights = [1/2]).

#### Examples::

```
p = 3
c = [1 for i=0:p]
pol = ImmutablePolynomial(c,:z)
Ipol = integrate(pol)
n = 10

x1=0.0
x2=5.0
x = collect(range(x1, x2, n))
f = pol.(x .-2.5)

w3 = trapezoidal_epw(3)
trapezoidal_integration(f, x1, x2, w3)
 15.416666666666673

Ipol(2.5)-Ipol(-2.5)
 15.41666666666666
```
