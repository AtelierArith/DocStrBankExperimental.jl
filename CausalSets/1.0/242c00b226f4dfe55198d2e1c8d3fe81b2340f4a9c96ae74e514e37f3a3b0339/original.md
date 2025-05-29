```
in_past_of(manifold, x, y) -> Bool
```

Test whether the point specified by coordinates `x` lies in the past light cone of the point specified by coordinates `y`.

Specifically, this function returns `true` iff the proper time between `x` and `y` is greater or equal to zero, and `x` lies in the past of `y`. In particular, it returns true if `x` is equal to `y`. This makes it equivalent to the causet ordering relation $x \preceq y$.
