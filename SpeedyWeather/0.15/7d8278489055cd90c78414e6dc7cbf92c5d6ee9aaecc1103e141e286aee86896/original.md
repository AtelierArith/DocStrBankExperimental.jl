The simplified Betts-Miller convection scheme from Frierson, 2007, https://doi.org/10.1175/JAS3935.1. This implements the qref-formulation in their paper. Fields and options are

  * `nlayers::Int64`: number of vertical layers
  * `time_scale::Dates.Second`: [OPTION] Relaxation time for profile adjustment
  * `relative_humidity::Any`: [OPTION] Relative humidity for reference profile
  * `surface_temp_humid::Any`: [OPTION] Surface perturbation of temp, humid to calculate the moist pseudo adiabat
