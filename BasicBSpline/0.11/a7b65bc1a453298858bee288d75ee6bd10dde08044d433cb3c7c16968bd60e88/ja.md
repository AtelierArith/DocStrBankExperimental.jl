```
bsplinebasis′(::AbstractFunctionSpace, ::Integer, ::Real) -> Real
```

Bスプライン基底関数の1階導関数。修正版。

$$
\dot{B}_{(i,p,k)}(t)
=p\left(\frac{1}{k_{i+p}-k_{i}}B_{(i,p-1,k)}(t)-\frac{1}{k_{i+p+1}-k_{i+1}}B_{(i+1,p-1,k)}(t)\right)
$$

`bsplinebasis′(P, i, t)` は `bsplinebasis(derivative(P), i, t)` と同等です。
