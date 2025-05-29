```
run(sim::FrequencySimulation, region::Shape;
    res=20, xres=res, yres=res, basis_order=5)
```

Run the simulation `sim` for a grid of positions in region and for angular frequency `ω`.

Frequency can be a float or vector of floats. The resolution of the grid points is defined by xres and yres.
