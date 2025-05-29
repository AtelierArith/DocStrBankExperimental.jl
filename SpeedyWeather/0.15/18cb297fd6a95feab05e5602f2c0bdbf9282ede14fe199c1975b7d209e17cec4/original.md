Spectral filter for horizontal diffusion. Fields are: 

  * `trunc::Int64`: spectral resolution
  * `nlayers::Int64`: number of vertical levels
  * `shift::Any`: [OPTION] shift diffusion to higher (positive shift) or lower (neg) wavenumbers, relative to trunc
  * `scale::Any`: [OPTION] Scale-selectiveness, steepness of the sigmoid, higher is more selective
  * `time_scale::Dates.Second`: [OPTION] diffusion time scale
  * `time_scale_div::Dates.Second`: [OPTION] stronger diffusion time scale for divergence
  * `resolution_scaling::Any`: [OPTION] resolution scaling to shorten time_scale with trunc
  * `power::Any`: [OPTION] power of the tanh function
  * `power_div::Any`: [OPTION] power of the tanh function for divergence
  * `expl::Any`
  * `impl::Any`
  * `expl_div::Any`
  * `impl_div::Any`
