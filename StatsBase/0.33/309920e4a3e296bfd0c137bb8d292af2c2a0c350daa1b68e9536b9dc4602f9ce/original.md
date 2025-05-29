```
competerank(x; lt=isless, by=identity, rev::Bool=false, ...)
```

Return the [standard competition ranking](http://en.wikipedia.org/wiki/Ranking#Standard_competition_ranking_.28.221224.22_ranking.29) ("1224" ranking) of an array. Supports the same keyword arguments as the `sort` function. Equal (*"tied"*) items are given the same rank, and the next rank comes after a gap that is equal to the number of tied items - 1. Missing values are assigned rank `missing`.
