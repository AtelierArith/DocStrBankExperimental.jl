```
cutord!(t::TPS{T}, t1::TPS{T}, order::Integer) where {T} -> t
```

Cuts out the monomials in `t1` at the given order and above. Or, if `order`  is negative, will cut monomials with orders at and below `abs(order)`. `t`  is set to the result. See the documentation for `cutord` for examples.
