```julia
modelage(mineral::SphericalAr, Tsteps, dm::Diffusivity)
modelage(mineral::PlanarAr, Tsteps, dm::Diffusivity)
```

Calculate the precdicted bulk K/Ar age of a mineral that has experienced a given  t-T path (specified by `mineral.tsteps` for time and `Tsteps` for temperature,  at a time resolution of `step(mineral.tsteps)`) using a Crank-Nicholson diffusion  solution for a spherical (or planar slab) grain of radius (or halfwidth ) `mineral.r`  at spatial resolution `mineral.dr`.

Spherical implementation based on the the Crank-Nicolson solution for diffusion out of a spherical mineral crystal in Ketcham, 2005 (doi: 10.2138/rmg.2005.58.11).
