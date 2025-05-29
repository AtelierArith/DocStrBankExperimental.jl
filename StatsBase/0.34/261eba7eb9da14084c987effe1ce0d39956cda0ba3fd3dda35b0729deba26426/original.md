```
tiedrank(x; lt=isless, by=identity, rev::Bool=false, ...)
```

Return the [tied ranking](http://en.wikipedia.org/wiki/Ranking#Fractional_ranking_.28.221_2.5_2.5_4.22_ranking.29), also called fractional or "1 2.5 2.5 4" ranking, of an array. Supports the same keyword arguments as the `sort` function. Equal (*"tied"*) items receive the mean of the ranks they would have been assigned under the ordinal ranking (see [`ordinalrank`](@ref)). Missing values are assigned rank `missing`.
