```
breakeven(yield, cashflows::Vector)
breakeven(yield, cashflows::Vector,times::Vector)
```

Calculate the time when the accumulated cashflows breakeven given the yield.

Assumptions:

  * cashflows occur at the end of the period
  * cashflows evenly spaced with the first one occuring at time zero if `times` not given

Returns `nothing` if cashflow stream never breaks even.

```julia
julia> breakeven(0.10, [-10,1,2,3,4,8])
5

julia> breakeven(0.10, [-10,15,2,3,4,8])
1

julia> breakeven(0.10, [-10,-15,2,3,4,8]) # returns the `nothing` value


```
