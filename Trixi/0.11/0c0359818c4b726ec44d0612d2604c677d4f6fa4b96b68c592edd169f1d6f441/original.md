```
FluxHydrostaticReconstruction(numerical_flux, hydrostatic_reconstruction)
```

!!! warning "Experimental code"
    This numerical flux is experimental and may change in any future release.


Allow for some kind of hydrostatic reconstruction of the solution state prior to the surface flux computation. This is a particular strategy to ensure that the method remains well-balanced for the shallow water equations, see [`ShallowWaterEquations1D`](@ref) or [`ShallowWaterEquations2D`](@ref).

For example, the hydrostatic reconstruction from Audusse et al. is implemented in one and two spatial dimensions, see [`hydrostatic_reconstruction_audusse_etal`](@ref) or the original paper

  * Emmanuel Audusse, François Bouchut, Marie-Odile Bristeau, Rupert Klein, and Benoit Perthame (2004) A fast and stable well-balanced scheme with hydrostatic reconstruction for shallow water flows [DOI: 10.1137/S1064827503431090](https://doi.org/10.1137/S1064827503431090)

Other hydrostatic reconstruction techniques are available, particularly to handle wet / dry fronts. A good overview of the development and application of hydrostatic reconstruction can be found in

  * Guoxian Chen and Sebastian Noelle A unified surface-gradient and hydrostatic reconstruction scheme for the shallow water equations (2021) [RWTH Aachen preprint](https://www.igpm.rwth-aachen.de/forschung/preprints/517)
  * Andreas Buttinger-Kreuzhuber, Zsolt Horváth, Sebastian Noelle, Günter Blöschl and Jürgen Waser (2019) A fast second-order shallow water scheme on two-dimensional structured grids over abrupt topography [DOI: 10.1016/j.advwatres.2019.03.010](https://doi.org/10.1016/j.advwatres.2019.03.010)
