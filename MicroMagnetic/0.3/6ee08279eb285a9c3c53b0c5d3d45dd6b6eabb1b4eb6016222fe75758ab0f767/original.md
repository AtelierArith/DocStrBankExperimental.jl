```
set_mu_s(sim::AtomisticSim, init::NumberOrArrayOrFunction)
```

Set the magnetic moment `mu_s` for the given atomistic system `sim`.

### Usage Examples

You can set a uniform magnetic moment for the entire system as follows:

```julia
set_mu_s(sim, 2 * mu_B)
```

Alternatively, you can use a function to define spatially varying magnetic moments. For example, to set a circular region with a specific magnetic moment:

```julia
function circular_shape(i, j, k, dx, dy, dz)
    if (i - 50.5)^2 + (j - 50.5)^2 <= 50^2
        return 2 * mu_B
    end
    return 0.0
end
set_mu_s(sim, circular_shape)
```

The `circular_shape` function here assigns `2 * mu_B` to atoms within a circle of radius 50 (in lattice units), centered at `(50.5, 50.5)`,      while setting it to `0.0` outside this region.
