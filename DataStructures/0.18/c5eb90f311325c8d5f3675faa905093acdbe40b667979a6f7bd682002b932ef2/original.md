```
 nsmallest(acc::Accumulator, [n])
```

Returns a sorted vector of the `n` least common elements, with their counts. If `n` is omitted, the full sorted collection is returned.

This is the opposite of the `nlargest` function. For obvious reasons this will not include zero counts for items not encountered. (unless those elements are added to he accumulator directly, eg via `acc[foo]=0)
