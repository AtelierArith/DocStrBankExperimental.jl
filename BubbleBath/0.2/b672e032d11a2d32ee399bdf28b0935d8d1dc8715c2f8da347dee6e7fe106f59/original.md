```
packing_fraction(radii::Vector{Real}, extent::NTuple{D,Real}) where D
```

Evaluate the packing fraction of a collection of spheres with radii `radii` in domain `extent`. This measurement is not exact if spheres are overlapping or cross through the domain boundaries.
