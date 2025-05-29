```
intersection(X::Interval, hs::HalfSpace)
```

Compute the intersection of an interval and a half-space.

### Input

  * `X`  – interval
  * `hs` – half-space

### Output

If the sets do not intersect, the result is the empty set. If the interval is fully contained in the half-space, the result is the original interval. Otherwise the result is the interval that describes the intersection.

### Algorithm

We first handle the special case that the normal vector `a` of `hs` is close to zero. Then we distinguish the cases that `hs` is a lower or an upper bound.
