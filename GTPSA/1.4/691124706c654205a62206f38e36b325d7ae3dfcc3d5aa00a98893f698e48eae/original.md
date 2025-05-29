```
cutord(t1::TPS, order::Integer)
```

Cuts out the monomials in `t1` at the given order and above. Or, if `order`  is negative, will cut monomials with orders at and below `abs(order)`.

# Examples

```julia-repl
julia> d = Descriptor(1, 10);

julia> Δx = first(@vars(d));

julia> cutord(sin(Δx), 5)
TPS64{Descriptor(NV=1, MO=10)}:
 Coefficient                Order   Exponent
  1.0000000000000000e+00      1      1
 -1.6666666666666666e-01      3      3


julia> cutord(sin(Δx), -5)
TPS64{Descriptor(NV=1, MO=10)}:
 Coefficient                Order   Exponent
 -1.9841269841269841e-04      7      7
  2.7557319223985893e-06      9      9
```
