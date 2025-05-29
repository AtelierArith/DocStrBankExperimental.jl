```
integral(f::RelPowerSeriesRingElem{T})
```

Return the integral of the power series $f$.

```
julia> R, x = power_series_ring(QQ, 10, :x)
(Univariate power series ring in x over Rationals, x + O(x^11))

julia> f = 2 + x + 3x^3
2 + x + 3*x^3 + O(x^10)

julia> integral(f)
2*x + 1//2*x^2 + 3//4*x^4 + O(x^11)
```
