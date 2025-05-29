```
AffineMap(trans::Transformation, x0)
```

Create an affine transformation corresponding to the differential transformation of `x0 + dx` according to `trans`, i.e. the Affine transformation that is locally most accurate in the vicinity of `x0`.
