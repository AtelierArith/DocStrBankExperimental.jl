```julia
RossbyNumber(
    model;
    location,
    add_background,
    dWdy_bg,
    dVdz_bg,
    dUdz_bg,
    dWdx_bg,
    dUdy_bg,
    dVdx_bg
)

```

Calculate the Rossby number using the vorticity in the rotation axis direction according to `model.coriolis`. Rossby number is defined as

```
    Ro = ωᶻ / f
```

where ωᶻ is the vorticity in the Coriolis axis of rotation and `f` is the Coriolis rotation frequency.
