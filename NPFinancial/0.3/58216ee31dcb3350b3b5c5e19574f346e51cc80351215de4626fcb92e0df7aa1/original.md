```
pmt(rate::Real, nper::Integer, pv::Real, fv = 0.0, when = :end)
```

Compute the payment given the present value `pv`, an interest rate `rate` that is compounded once per period, over `nper` number of periods, such that at the end of the last period the value becomes `fv`. The payment is expected to be paid at the beginning of each period (`:begin`) or `:end` of the period, as specified in the `when` argument.

# Examples

Let's say I have need to repay a mortage loan with amount 300000 (present value) with monthly interst rate of 4.25% over the next 30 years.  What would be my monthly payment?

```
julia> pmt(0.0425/12, 30*12, 300000)
-1475.8196732384283
```
