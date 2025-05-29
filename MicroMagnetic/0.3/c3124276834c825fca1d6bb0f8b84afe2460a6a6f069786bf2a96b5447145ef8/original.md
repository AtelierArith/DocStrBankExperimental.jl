```
add_anis(sim::AbstractSim, Ku::NumberOrArrayOrFunction; axis=(0,0,1), name="anis")
```

Add Anisotropy to the system, where the energy density is given by

$$
    E_\mathrm{anis} =  K_{u} (1 - \vec{m} \cdot \hat{u})^2
$$
