```
dim(K)
```

The dimension of `K`, defined as the maximum size of a face of `K` minus 1.

If `K` is the void complex (i.e. `K` has no faces), returns `-2` for type stability (this function always returns an `Int`); mathematically a sensible value would be `-Inf`.
