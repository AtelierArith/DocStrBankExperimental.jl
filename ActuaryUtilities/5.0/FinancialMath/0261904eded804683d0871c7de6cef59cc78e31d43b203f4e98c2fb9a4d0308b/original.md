```
duration(Macaulay(),interest_rate,cfs,times)
duration(Modified(),interest_rate,cfs,times)
duration(DV01(),interest_rate,cfs,times)
duration(interest_rate,cfs,times)             # Modified Duration
duration(interest_rate,valuation_function)    # Modified Duration
```

Calculates the Macaulay, Modified, or DV01 duration. `times` may be ommitted and the valuation will assume evenly spaced cashflows starting at the end of the first period.

Note that the calculated duration will depend on the periodicity convention of the `interest_rate`: a `Periodic` yield (or yield model with that convention) will be a slightly different computed duration than a `Continous` which follows from the present value differing according to the periodicity.

When not given `Modified()` or `Macaulay()` as an argument, will default to `Modified()`.

  * Modified duration: the relative change per point of yield change.
  * Macaulay: the cashflow-weighted average time.
  * DV01: the absolute change per basis point (hundredth of a percentage point).

# Examples

Using vectors of cashflows and times

```julia-repl
julia> times = 1:5;

julia> cfs = [0,0,0,0,100];

julia> duration(0.03,cfs,times)
4.854368932038835

julia> duration(Periodic(0.03,1),cfs,times)
4.854368932038835

julia> duration(Continuous(0.03),cfs,times)
5.0

julia> duration(Macaulay(),0.03,cfs,times)
5.0

julia> duration(Modified(),0.03,cfs,times)
4.854368932038835

julia> convexity(0.03,cfs,times)
28.277877274012614

```

Using any given value function: 

```julia-repl
julia> lump_sum_value(amount,years,i) = amount / (1 + i ) ^ years
julia> my_lump_sum_value(i) = lump_sum_value(100,5,i)
julia> duration(0.03,my_lump_sum_value)
4.854368932038835
julia> convexity(0.03,my_lump_sum_value)
28.277877274012617

```
