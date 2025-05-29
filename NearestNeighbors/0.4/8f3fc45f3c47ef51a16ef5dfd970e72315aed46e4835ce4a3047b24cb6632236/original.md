```
inrange(tree::NNTree, points, radius [, sortres=false]) -> indices
```

Find all the points in the tree which is closer than `radius` to `points`. If `sortres = true` the resulting indices are sorted.

See also: `inrange!`, `inrangecount`.
