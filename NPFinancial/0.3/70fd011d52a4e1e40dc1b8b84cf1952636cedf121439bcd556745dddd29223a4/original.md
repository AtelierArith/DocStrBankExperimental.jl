```
pv(rate::Real, nper::Integer, pmt::Real, fv = 0.0, when = :end)
```

Compute the present value given the future value `fv`, an interest rate `rate` and a fixed periodic payment `pmt` over a number of periods `nper`.  The payment is expected to be paid at the beginning of each period (`:begin`) or `:end` of the period, as specified in the `when` argument.
