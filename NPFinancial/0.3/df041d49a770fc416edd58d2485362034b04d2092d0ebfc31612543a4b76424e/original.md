```
npv(rate::Real, values::AbstractVector{<:Real})
```

Compute the Net Present Value (NPV) of a cash flow series `values` given an internal rate of return `rate`.

The (fixed) time interval between cash flow "events" must be the same as that for which `rate` is given (i.e., if `rate` is per year, then precisely a year is understood to elapse between each cash flow event).  By convention, investments or "deposits" are negative, income or "withdrawals" are positive; `values` must begin with the initial investment, thus `values[1]` will typically be negative.

# Examples

```
julia> npv(0.281,[-100, 39, 59, 55, 20])
-0.00847859163845488
```

# Reference

  * L. J. Gitman, "Principles of Managerial Finance, Brief," 3rd ed.,   Addison-Wesley, 2003, pg. 346.
