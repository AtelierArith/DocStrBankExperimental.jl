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

# 引数

  * `dims_by`: `by` が提供されている場合、`dims` の長さは1でなければなりません!
  * `dims`: mapslices によって使用されます
  * `combine`: true の場合、結果を大きな配列に結合します

# 例

```julia
using Ipaper
using NaNStatistics
using Distributions

dates = make_date(2010, 1, 1):Day(1):make_date(2010, 12, 31)
yms = format.(dates, "yyyy-mm")

## 例 01, R の aggregate と同様
x1 = rand(365)
apply(x1, 1, yms)
apply(x1, 1, by=yms)

## 例 02
n = 100
x = rand(n, n, 365)

res = apply(x, 3, by=yms)
size(res) == (n, n, 12)

res = apply(x, 3)
size(res) == (n, n)

## 例 03
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
