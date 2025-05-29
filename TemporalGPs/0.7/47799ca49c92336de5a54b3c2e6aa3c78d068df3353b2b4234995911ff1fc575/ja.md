```
Separable{Tl<:Kernel, Tr<:Kernel} <: Kernel
```

カーネル `k` は次のように定義されます。

```julia
k((xl, xr), (yl, yr)) = k.l(xl, yl) * k.r(xr, yr)
```
