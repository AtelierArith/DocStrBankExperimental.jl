```
set_Ms(sim::MicroSim, Ms::NumberOrArrayOrFunction)
```

研究対象のシステムの飽和磁化 Ms を設定します。例えば、

```julia
   set_Ms(sim, 8.6e5)
```

または

```julia
function circular_Ms(i,j,k,dx,dy,dz)
    if (i-50.5)^2 + (j-50.5)^2 <= 50^2
        return 8.6e5
    end
    return 0.0
end
set_Ms(sim, circular_Ms)
```
