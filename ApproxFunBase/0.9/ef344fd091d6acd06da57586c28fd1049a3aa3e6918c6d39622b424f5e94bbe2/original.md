```
lneumann(d::Domain) = ldiffbc(d, 1)
```

The neumann boundary condition on the left endpoint of `d`. See also [`rneumann`](@ref) and [`ldiffbc`](@ref).  
