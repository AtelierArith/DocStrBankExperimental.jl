```
set_pinning(sim::AbstractSim, ids::ArrayOrFunction)
```

Pinning the spins at the given ids.

```julia
function pinning_boundary(i,j,k,dx,dy,dz)
    if i == 1 || i == 100
        return true
    end
    return false
end
set_pinning(sim, pinning_boundary)
```
