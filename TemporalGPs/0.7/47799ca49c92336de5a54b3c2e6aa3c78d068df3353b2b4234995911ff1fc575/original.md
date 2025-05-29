```
Separable{Tl<:Kernel, Tr<:Kernel} <: Kernel
```

The kernel `k` given by

```julia
k((xl, xr), (yl, yr)) = k.l(xl, yl) * k.r(xr, yr)
```
