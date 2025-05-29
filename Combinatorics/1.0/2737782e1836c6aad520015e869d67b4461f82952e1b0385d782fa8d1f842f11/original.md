```
powerset(a, min=0, max=length(a))
```

Generate all subsets of an indexable object `a` including the empty set, with cardinality bounded by `min` and `max`. Because the number of subsets can be very large, this function returns an iterator object. Use `collect(powerset(a, min, max))` to get an array of all subsets.
