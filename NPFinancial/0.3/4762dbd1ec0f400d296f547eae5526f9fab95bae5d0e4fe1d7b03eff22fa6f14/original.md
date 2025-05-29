```
nper(rate::Real, pmt::Real, pv::Real, fv = 0.0, when = :end)
```

Compute how many periods the present value `pv` may accrue/repaid till the future value `fv` given a specific interest rate `rate` and a fixed payment `pmt`. The payment is expected to be paid at the beginning of each period (`:begin`) or `:end` of the period, as specified in the `when` argument.
