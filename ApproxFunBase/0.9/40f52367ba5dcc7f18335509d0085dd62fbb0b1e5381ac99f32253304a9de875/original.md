```
rneumann(d::Domain) = rdiffbc(d, 1)
```

The neumann boundary condition on the right endpoint of `d`. See also [`lneumann`](@ref) and [`rdiffbc`](@ref).  
