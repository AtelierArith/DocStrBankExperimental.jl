```
close!(p, neighbors)
```

Given a `Parcel` `p` and an adjacency list `neighbors`, perform a morphological closing to fill in gaps, if any, by finding vertices in `p` where all of its  neighbors but one belong to `p`. Note: for performance reasons, this may not be technically quite the same as a true closing operation, `erode!(dilate!(p))`.
