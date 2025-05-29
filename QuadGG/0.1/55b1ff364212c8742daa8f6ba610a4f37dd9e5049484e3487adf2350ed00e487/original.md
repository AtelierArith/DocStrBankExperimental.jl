```
adaptlob(f,a,b; tol::Real=1e-10, trace::Bool=false)
```

Numerically integrate `f` over the closed real interval `[a,b]` to within tolerance `tol` using the adaptive Gauss-Lobatto method from Gander and Gautschi (2000).

Passing `trace=true` prints out information about where the function is being sampled.

`f` must be defined at `a` and `b`.

```
using QuadGG
adaptlob(sqrt,0,1)
```
