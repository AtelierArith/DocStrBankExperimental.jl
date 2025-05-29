```
trapezoidal_integration(f, x1, x2, weights)
```

タブ化された関数 $f=[f_0,⋯\ f_n]$ の $x1 ≤ x ≤ x2$ の範囲での積分を、重みベクトル `weights` による端点補正を伴う最適化された台形法を使用して計算します。

$$
    ∫_0^n f(x) dx = a_1 (f_0+f_n) + ⋯ + a_k (f_{k-1}+f_{n-k+1})
                                                         + (f_k+⋯+f_{n-k}).
$$

この法則は、次数 $d=0,\ 1,⋯\ k-1$ の多項式に対して正確です。$k=1$ の場合、この法則は通常の台形法に簡略化されます（weights = [1/2]）。

#### 例::

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
