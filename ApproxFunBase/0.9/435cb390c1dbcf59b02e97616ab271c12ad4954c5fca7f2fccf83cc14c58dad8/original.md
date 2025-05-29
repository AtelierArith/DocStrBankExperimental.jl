```
ldirichlet(d::Domain) = ldiffbc(d, 0)
```

The dirichlet boundary condition on the left endpoint of `d`. See also [`rdirichlet`](@ref) and [`ldiffbc`](@ref).
