```
mirr(values::AbstractVector{<:Real}, finance_rate::Real, reinvest_rate::Real)
```

Compute the modified internal rate of return (MIRR) given a series of cash flows, a `finance_rate` (interest rate paid on the cash flows) and `reinvest_rate` (interest rate received on the cash flows upon reinvestment).
