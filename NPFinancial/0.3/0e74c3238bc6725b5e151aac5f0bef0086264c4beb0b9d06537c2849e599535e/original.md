```
fv(rate::Real, nper::Integer, pmt::Real, pv::Real, when = :end)
```

Compute the future value given the present value `pv`, an interest rate `rate` that is compounded once per period, over `nper` number of periods. A fixed payment `pmt` may be specified in the `when` argument, which is paid either at the beginning of each period (`:begin`) or `:end` of the period.

# Examples

```
julia> fv(0.05, 1, 0, -100)
105.0

julia> fv(0.05, 2, 0, -100)
110.25
```
