```
swap(cap::Intersection)
```

Return a new `Intersection` object with the arguments swapped.

### Input

  * `cap` – intersection of two sets

### Output

A new `Intersection` object with the arguments swapped. The old cache is shared between the old and new objects.

### Notes

The advantage of using this function instead of manually swapping the arguments is that the cache is shared.
