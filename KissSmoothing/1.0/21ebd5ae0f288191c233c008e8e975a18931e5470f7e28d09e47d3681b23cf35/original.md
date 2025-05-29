```
lsq_denoise(S::AbstractVector{<:Real}; order::Integer=3, strength::Real = NaN)
```

denoise a sequence S by penalising its order-th finite differences in a least squares regression

```
`S` : sequence.

Keyword arguments:

`order` : finite differencing order.

`strength` : intensity of penalisation on the derivative in [0, Inf[, if unspecified it is auto-determined.
```

return the filtered sequence.
