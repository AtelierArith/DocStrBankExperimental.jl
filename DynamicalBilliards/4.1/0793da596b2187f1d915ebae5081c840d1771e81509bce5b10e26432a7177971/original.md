```
raysplit_indices(bd::Billiard, raysplitters::Tuple)
```

Create a vector of integers. The `i`th entry tells you which entry of the `raysplitters` tuple is associated with the `i`th obstacle of the billiard.

If the `i`th entry is `0`, this means that the obstacle does not do raysplitting.
