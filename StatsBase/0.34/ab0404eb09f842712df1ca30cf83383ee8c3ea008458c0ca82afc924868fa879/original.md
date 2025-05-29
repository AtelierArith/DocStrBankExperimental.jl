```
quantilerank(itr, value; method=:inc)
```

Compute the quantile position in the [0, 1] interval of `value` relative to collection `itr`.

Different definitions can be chosen via the `method` keyword argument. Let `count_less` be the number of elements of `itr` that are less than `value`, `count_equal` the number of elements of `itr` that are equal to `value`, `n` the length of `itr`, `greatest_smaller` the highest value below `value` and `smallest_greater` the lowest value above `value`. Then `method` supports the following definitions:

  * `:inc` (default): Return a value in the range 0 to 1 inclusive. Return `count_less / (n - 1)` if `value ∈ itr`, otherwise apply interpolation based on definition 7 of quantile in Hyndman and Fan (1996) (equivalent to Excel `PERCENTRANK` and `PERCENTRANK.INC`). This definition corresponds to the lower semi-continuous inverse of [`quantile`](@ref) with its default parameters.
  * `:exc`: Return a value in the range 0 to 1 exclusive. Return `(count_less + 1) / (n + 1)` if `value ∈ itr` otherwise apply interpolation based on definition 6 of quantile in Hyndman and Fan (1996) (equivalent to Excel `PERCENTRANK.EXC`).
  * `:compete`: Return `count_less / (n - 1)` if `value ∈ itr`, otherwise return `(count_less - 1) / (n - 1)`, without interpolation (equivalent to MariaDB `PERCENT_RANK`, dplyr `percent_rank`).
  * `:tied`: Return `(count_less + count_equal/2) / n`, without interpolation. Based on the definition in Roscoe, J. T. (1975) (equivalent to `"mean"` kind of SciPy `percentileofscore`).
  * `:strict`: Return `count_less / n`, without interpolation (equivalent to `"strict"` kind of SciPy `percentileofscore`).
  * `:weak`: Return `(count_less + count_equal) / n`, without interpolation (equivalent to `"weak"` kind of SciPy `percentileofscore`).

!!! note
    An `ArgumentError` is thrown if `itr` contains `NaN` or `missing` values or if `itr` contains fewer than two elements.


# References

Roscoe, J. T. (1975). [Fundamental Research Statistics for the Behavioral Sciences](http://www.bryanburnham.net/wp-content/uploads/2014/07/Fundamental-Statistics-for-the-Behavioral-Sciences-v2.0.pdf#page=57)", 2nd ed., New York : Holt, Rinehart and Winston.

Hyndman, R.J and Fan, Y. (1996) "[Sample Quantiles in Statistical Packages](https://www.amherst.edu/media/view/129116/original/Sample+Quantiles.pdf)", *The American Statistician*, Vol. 50, No. 4, pp. 361-365.

# Examples

```julia-repl
julia> using StatsBase

julia> v1 = [1, 1, 1, 2, 3, 4, 8, 11, 12, 13];

julia> v2 = [1, 2, 3, 5, 6, missing, 8];

julia> v3 = [1, 2, 3, 4, 4, 5, 6, 7, 8, 9];

julia> quantilerank(v1, 2)
0.3333333333333333

julia> quantilerank(v1, 2, method=:exc), quantilerank(v1, 2, method=:tied)
(0.36363636363636365, 0.35)

# use `skipmissing` for vectors with missing entries.
julia> quantilerank(skipmissing(v2), 4)
0.5

# use broadcasting with `Ref` to compute quantile rank for multiple values
julia> quantilerank.(Ref(v3), [4, 8])
2-element Vector{Float64}:
 0.3333333333333333
 0.8888888888888888
```
