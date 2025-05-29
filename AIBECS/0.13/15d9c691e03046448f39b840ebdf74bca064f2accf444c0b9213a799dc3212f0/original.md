```
FATO(w_top, Iabove)
```

Build the `FATO` operator for a particle sinking speed `w_top`

(`w_top` is the sinking speed at the top of each grid cell.)

The `FATO` operator is defined by

```
FATO * x = w_top * x(above) ≈ ϕ_top.
```
