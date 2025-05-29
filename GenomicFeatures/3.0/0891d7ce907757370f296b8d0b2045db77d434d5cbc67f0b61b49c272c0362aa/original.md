```
eachoverlap(intervals_a, intervals_b, [groupname_isless=Base.isless])
```

Create an iterator of overlapping intervals between `intervals_a` and `intervals_b`.

This function assumes elements of `intervals_a` and `intervals_b` are sorted by its group name and left position. If the element type is not a subtype of `GenomicFeatures.AbstractGenomicInterval`, elements are converted to `GenomicInterval` objects.

The third optional argument is a function that defines the order of the group names. The default function is `Base.isless`, which is the lexicographical order.
