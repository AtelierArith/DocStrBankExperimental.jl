The simplified Betts-Miller convection scheme from Frierson, 2007, https://doi.org/10.1175/JAS3935.1 but with humidity set to zero. Fields and options are

  * `nlayers::Int64`: number of vertical layers/levels
  * `time_scale::Dates.Second`: [OPTION] Relaxation time for profile adjustment
  * `surface_temp::Any`: [OPTION] Surface perturbation of temp to calculate the dry adiabat
