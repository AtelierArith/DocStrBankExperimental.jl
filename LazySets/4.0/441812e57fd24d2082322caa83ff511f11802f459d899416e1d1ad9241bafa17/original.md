```
intersection(X::Interval, Y::LazySet)
```

Compute the intersection of an interval and a convex set.

### Input

  * `X` – interval
  * `Y` – convex set

### Output

If the sets do not intersect, the result is the empty set. Otherwise the result is the interval that describes the intersection, which may be of type `Singleton` if the intersection is very small.
