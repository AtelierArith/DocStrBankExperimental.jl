```
ppmt(rate, per, nper, pv, fv = 0.0, when = :end)
```

Compute the principal component of the periodic payment.  This useful for any loan that has a repayment schedule.

# Examples

```
julia> pmt(0.0425/12, 30*12, 300000)
-1475.8196732384283

julia> ppmt.(0.0425/12, [1,2,3,358,359,360], 30*12, 300000)
6-element Array{Float64,1}:
  -413.32
  -414.784
  -416.253
 -1460.25
 -1465.42
 -1470.61
```
