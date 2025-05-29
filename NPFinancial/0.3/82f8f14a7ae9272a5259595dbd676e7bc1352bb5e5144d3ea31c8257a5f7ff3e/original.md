```
ipmt(rate::Real, per::Integer, nper::Integer, pv::Real, fv = 0.0, when = :end)
```

Compute the interest component of the periodic payment.  This useful for any loan that has a repayment schedule.

# Examples

Let's say I have need to repay a mortage loan with amount 300000 (present value) with monthly interst rate of 4.25% over the next 30 years.  What would be the interest component of my monthly payment?  Initially, the interest component is a large part of the payment but towards the end, it would be a smaller portion as illustrated below for periods 1, 2, 3, 358, 359, and 360:

```
julia> pmt(0.0425/12, 30*12, 300000)
-1475.8196732384283

julia> ipmt.(0.0425/12, [1,2,3,358,359,360], 30*12, 300000)
6-element Array{Float64,1}:
 -1062.5
 -1061.04
 -1059.57
   -15.5702
   -10.3984
    -5.20841
```
