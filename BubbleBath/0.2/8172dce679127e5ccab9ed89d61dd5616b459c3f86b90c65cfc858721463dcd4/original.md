```
walkmap(
    spheres::AbstractVector{Sphere{D}}, extent::NTuple{D,<:Real},
    resolution::Real, probe_radius::Real = 0;
    boundaries::Symbol = :cut
) where D
```

Generate a walkmap for the given configuration of `spheres` in the domain `extent`, with the desired `resolution.` A positive `probe_radius` restricts the walkable space assuming that the "probe" has a finite size. 

`boundaries` can be set to `:cut` or `:wrap` to define how to deal with spheres that cross through the domain boundaries (in case there is any).
