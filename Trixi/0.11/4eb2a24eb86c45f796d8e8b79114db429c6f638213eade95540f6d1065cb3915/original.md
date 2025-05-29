```
flux(u, orientation_or_normal, equations)
```

Given the conservative variables `u`, calculate the (physical) flux in Cartesian direction `orientation::Integer` or in arbitrary direction `normal::AbstractVector` for the corresponding set of governing `equations`. `orientation` is `1`, `2`, and `3` for the x-, y-, and z-directions, respectively.
