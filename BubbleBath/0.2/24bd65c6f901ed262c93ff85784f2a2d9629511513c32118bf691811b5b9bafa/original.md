```
packing_fraction(spheres::Vector{Sphere{D}}, extent::NTuple{D,Real}) where D
```

Evaluate the packing fraction of `spheres` in domain `extent`. This measurement is not exact if spheres are overlapping or cross through the domain boundaries.
