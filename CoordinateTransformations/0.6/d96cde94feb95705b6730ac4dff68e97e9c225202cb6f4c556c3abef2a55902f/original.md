```
AffineMap <: AbstractAffineMap
```

A concrete affine transformation.  To construct the mapping `x -> M*x + v`, use

```
AffineMap(M, v)
```

where `M` is a matrix and `v` a vector.  An arbitrary `Transformation` may be converted into an affine approximation by linearizing about a point `x` using

```
AffineMap(trans, [x])
```

For transformations which are already affine, `x` may be omitted.
