```
automatic_Δt_basins(ds::DynamicalSystem, grid; N = 5000) → Δt
```

Calculate an optimal `Δt` value for [`basins_of_attraction`](@ref). This is done by evaluating the dynamic rule `f` (vector field) at `N` randomly chosen points within the bounding box of the grid. The average `f` is then compared with the average diagonal length of a grid cell and their ratio provides `Δt`.

Notice that `Δt` should not be too small which happens typically if the grid resolution is high. It is okay if the trajectory skips a few cells. Also, `Δt` that is smaller than the internal step size of the integrator will cause a performance drop.
