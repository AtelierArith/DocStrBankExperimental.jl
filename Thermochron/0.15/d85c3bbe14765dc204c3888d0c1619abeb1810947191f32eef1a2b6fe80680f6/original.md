```julia
modelage(mineral::ZirconHe, Tsteps, [ρᵣ], dm::ZRDAAM)
modelage(mineral::ApatiteHe, Tsteps, [ρᵣ], dm::RDAAM)
modelage(mineral::SphericalHe, Tsteps, dm::Diffusivity)
modelage(mineral::PlanarHe, Tsteps, dm::Diffusivity)
```

Calculate the predicted bulk U-Th/He age of a zircon, apatite, or other mineral that has experienced a given t-T path (specified by `mineral.tsteps` for time and `Tsteps` for temperature, at a time resolution of `step(mineral.tsteps)`)  using a Crank-Nicolson diffusion solution for a spherical (or planar slab) grain of radius (or halfwidth) `mineral.r` at spatial resolution `mineral.dr`.

Spherical implementation based on the the Crank-Nicolson solution for diffusion out of a spherical mineral crystal in Ketcham, 2005 (doi: 10.2138/rmg.2005.58.11).
