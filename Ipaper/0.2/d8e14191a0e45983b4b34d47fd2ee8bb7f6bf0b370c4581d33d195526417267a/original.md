```julia
apply(A::AbstractArray; ...) -> Any
apply(
    A::AbstractArray,
    dims_by,
    args...;
    dims,
    by,
    fun,
    combine,
    parallel,
    progress,
    kw...
) -> Any

```

# Arguments

  * `dims_by`: if `by` provided, the length of `dims` should be one!
  * `dims`: used by mapslices
  * `combine`: if true, combine the result to a large array

# Examples

```julia
using Ipaper
using NaNStatistics
using Distributions

dates = make_date(2010, 1, 1):Day(1):make_date(2010, 12, 31)
yms = format.(dates, "yyyy-mm")

## example 01, some as R aggregate
x1 = rand(365)
apply(x1, 1, yms)
apply(x1, 1, by=yms)

## example 02
n = 100
x = rand(n, n, 365)

res = apply(x, 3, by=yms)
size(res) == (n, n, 12)

res = apply(x, 3)
size(res) == (n, n)

## example 03
dates = make_date(2010):Day(1):make_date(2013, 12, 31)
n = 10
ntime = length(dates)
x = rand(n, n, ntime, 13)

years = year.(dates)
res = apply(x, 3; by=years, fun=_nanquantile, combine=true, probs=[0.05, 0.95])
obj_size(res)

res = apply(x, 3; by=years, fun=mean, combine=true)

apply(x, 3; by = month.(dates), fun=slope_mk)
```
