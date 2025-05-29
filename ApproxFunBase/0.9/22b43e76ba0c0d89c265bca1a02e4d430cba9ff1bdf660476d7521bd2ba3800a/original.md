```
rdirichlet(d::Domain) = rdiffbc(d, 0)
```

The dirichlet boundary condition on the right endpoint of `d`. See also [`ldirichlet`](@ref) and [`rdiffbc`](@ref).
