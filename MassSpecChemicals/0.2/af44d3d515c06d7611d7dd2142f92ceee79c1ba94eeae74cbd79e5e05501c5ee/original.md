```
real_interval(val, lop = <=, rop = <=)
real_interval(ct::Criteria, lop = <=, rop = <=)
real_interval(val::Missing, lop = <=, rop = <=) = missing
real_interval(val::RealIntervals, lop = <=, rop = <=) = val
```

Construct a `RealInterval`.

When a value aside from `missing`, criteria, and real interval is given, it constructs a real interval from `-abs(val)` to `abs(val)`.

When a criteira is given, it constructs a criteria whose criteria values become real intervals.

# Examples

```julia
julia> ct = Criteria(10, 0.2);

julia> peak_crit = real_interval(ct);

julia> qualified_peak(x, x̂, ct) = all(c -> in(x - x̂, c), ct(x̂)); # The difference of x and x̂ should be within ±10 and ±20%

julia> peak_crit(100) # create criteria with true value 100
([-10, 10], [-20, 20])

julia> peak_crit(10) # create criteria with true value 10
([-10, 10], [-2, 2])

julia> qualified_peak(85, 100, peak_crit)
false

julia> qualified_peak(9, 10, peak_crit)
true 

```
