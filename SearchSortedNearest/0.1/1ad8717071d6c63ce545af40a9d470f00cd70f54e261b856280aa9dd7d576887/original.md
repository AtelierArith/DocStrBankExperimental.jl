```
searchsortednearest(a, x; by=<transform>, lt=<comparison>, distance=(a,b) -> abs(a-b), rev=false)
```

Find the index of (sorted) collection `a` that has the smallest `distance` to `x`.   Ties go to the smallest index.

# Examples

```
using SearchSortedNearest

searchsortednearest(1:10, 1.1) == 1
searchsortednearest(1:10, 1.9) == 2
```
