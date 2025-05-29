```
set_Ms(sim::MicroSim, Ms::NumberOrArrayOrFunction)
```

Set the saturation magnetization Ms of the studied system. For example,

```julia
   set_Ms(sim, 8.6e5)
```

or

```julia
function circular_Ms(i,j,k,dx,dy,dz)
    if (i-50.5)^2 + (j-50.5)^2 <= 50^2
        return 8.6e5
    end
    return 0.0
end
set_Ms(sim, circular_Ms)
```
