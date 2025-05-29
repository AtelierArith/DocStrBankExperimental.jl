```
TetrahedralLimits(a::NTuple{d}) where d
```

A parametrization of the integration limits for a tetrahedron whose vertices are

```
( 0.0,  0.0, ...,  0.0)
( 0.0,  0.0, ..., a[d])
…
( 0.0, a[2], ..., a[d])
(a[1], a[2], ..., a[d])
```
