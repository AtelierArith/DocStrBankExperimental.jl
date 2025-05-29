```
ArraySlice(array::AbstractArray, interval::UnitRange)
```

Creates a new array slice pointing to the hence array shifted by the starting  value of the interval. This is faster than a view, and has better performance when iterating over it.

Note: It doesn't allow you to use out of bounds indices
