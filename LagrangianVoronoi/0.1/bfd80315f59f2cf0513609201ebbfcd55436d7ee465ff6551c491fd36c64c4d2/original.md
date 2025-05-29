```
fourier_step!(grid::VoronoiGrid, dt::Float64)
```

Update the energy of Voronoi polygon by Fourier heat conduction.  This assumes that every polygon `p` has its value of heat conductivity `p.k` assigned by the initial condition or otherwise.
