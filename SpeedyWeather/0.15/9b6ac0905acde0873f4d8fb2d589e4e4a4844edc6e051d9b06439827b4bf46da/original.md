Horizontal hyper diffusion of vor, div, temp, humid; implicitly in spectral space with a `power` of the Laplacian (default = 4) and the strength controlled by `time_scale` (default = 1 hour). For vorticity and divergence, by default, the `time_scale` (=1/strength of diffusion) is reduced with increasing resolution through `resolution_scaling` and the power is linearly decreased in the vertical above the `tapering_σ` sigma level to `power_stratosphere` (default 2).

For the BarotropicModel and ShallowWaterModel no tapering or scaling is applied. Fields and options are

  * `trunc::Int64`: spectral resolution
  * `nlayers::Int64`: number of vertical levels
  * `power::Any`: [OPTION] power of Laplacian
  * `time_scale::Dates.Second`: [OPTION] diffusion time scale
  * `time_scale_div::Dates.Second`: [OPTION] diffusion time scale for temperature and humidity
  * `resolution_scaling::Any`: [OPTION] stronger diffusion with resolution? 0: constant with trunc, 1: (inverse) linear with trunc, etc
  * `power_stratosphere::Any`: [OPTION] different power for tropopause/stratosphere
  * `tapering_σ::Any`: [OPTION] linearly scale towards power_stratosphere above this σ
  * `expl::Any`
  * `impl::Any`
  * `expl_div::Any`
  * `impl_div::Any`
