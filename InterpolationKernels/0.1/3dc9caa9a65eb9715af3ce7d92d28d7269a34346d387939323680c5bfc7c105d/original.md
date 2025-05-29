```
KeysSplinePrime([T=Float64,] a, B=Flat)
```

yields a kernel instance that is the 1st derivative of the Keys kernel (see [`KeysSpline`](@ref)) for floating-point type `T`, parameter `a` and boundary conditions `B`.  This derivative is given by:

```
ker′(x) = p′(abs(x))*sign(x)   if abs(x) ≤ 1
          q′(abs(x))*sign(x)   if 1 ≤ abs(x) ≤ 2
          0                    if abs(x) ≥ 2
```

with:

```
p(x) = -2*(a + 3)*x + 3*(a + 2)*x^2
q(x) = 8a - 10a*x + 3a*x^2
```
