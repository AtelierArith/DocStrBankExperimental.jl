```
CountMap(T::Type)
CountMap(dict::AbstractDict{T, Int})
```

Track a dictionary that maps unique values to its number of occurrences.  Similar to `StatsBase.countmap`.

Counts can be incremented by values other than one (and decremented) using the `fit!(::CountMap{T}, ::Pair{T,Int})` method, e.g.

```julia
o = fit!(CountMap(String), ["A", "B"])
fit!(o, "A" => 5)
fit!(o, "A" => -1)
```

# Example

```
o = fit!(CountMap(Int), rand(1:10, 1000))
value(o)
OnlineStatsBase.probs(o)
OnlineStats.pdf(o, 1)
collect(keys(o))
sort!(o)
delete!(o, 1)
```
