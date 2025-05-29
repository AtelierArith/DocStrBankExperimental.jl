```julia
implicit_relax_h!(d)
implicit_relax_h!(d, interval_bnds)

```

`h(x,p) = 0` で定義される `x(p)` の緩和を計算します。ここで、`h` は `h(out, x, p)` として指定されます。
