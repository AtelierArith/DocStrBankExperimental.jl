```
SPAC
```

An instance of a soil-plant-atmopsheric continuum model with the following fields:

  * `reference_date`: DateTime to relate internal use of numerical days to real-world dates
  * `tspan`: Tuple `(0, Int)` Time span of available input data in days since reference date
  * `solver_options`: `NamedTuple`: (compute*intermediate*quantities, simulate_isotopes, DTIMAX, DSWMAX, DPSIMAX), containing some solver options for the model
  * `soil_discretization`: `DataFrame` with contents from `soil_discretizations.csv`, i.e. containing columns:       `Upper_m`,`Lower_m`,`Rootden_`,`uAux_PSIM_init_kPa`,`u_delta18O_init_permil`,`u_delta2H_init_permil`

    ```
      Either loaded from `soil_discretizations.csv` or then specified as argument to loadSPAC().
      Unused values are NaN.
    ```
  * `forcing`: `NamedTuple`: (:meteo, :meteo_iso, :storm_durations), containing atmospheric forcings

      * `forcing.meteo`: DataFrame with daily atmospheric variables
      * `forcing.meteo_iso`: DataFrame with isotopic signatures of precipitation
      * `forcing.storm_durations`: DataFrame with approximate typical storm duration in hours for each month
  * `pars`: `NamedTuple`: (:params, )

      * `pars.params`: `NamedTuple`: (), containing scalar parameter values for the model
      * `pars.root_distribution`: either:

          * `NamedTuple`: (beta, theta, z_rootMax_m = nothing) parametrization of root distribution with depth (f(z_m) with z_m in meters and negative downward)."
          * `NamedTuple`: (alpha = 0.97, z_rootMax_m = nothing) parametrization of root distribution with depth (f(z_m) with z_m in meters and negative downward)."
          * or String: `"soil_discretization.csv"` meaning that it must be defined in `soil_discretizations.csv`
      * `pars.IC_scalar`: `NamedTuple`: (), containing initial conditions of the scalar state variables
      * `pars.IC_soil`: initial conditions of the state variables (scalar or related to the soil). Either:

          * `NamedTuple`: (PSIM_init, δ18O_init, δ2H_init), containing constant values for the initial conditions
          * [NOT IMPELMENTED:]`NamedTuple`: (PSIM_init, δ18O_init, δ2H_init), containing functions of the initial values with argument Δz
          * or String: `"soil_discretization.csv"` meaning that it must be defined in `soil_discretizations.csv`
      * `pars.canopy_evolution`: canopy parameters (LAI, SAI, DENSEF, HEIGHT) as relative in percent. Either:

          * `NamedTuple`: (DENSEF*rel = 100, HEIGHT*rel = 100, SAI*rel = 100, LAI*rel = (DOY_Bstart, Bduration, DOY_Cstart, Cduration, LAI_perc_BtoC, LAI_perc_CtoB)), containing constant values and parameters for LAI_relative interpolation
          * or DataFrame: with daily values
      * `pars.soil_horizons`: DataFrame containing description of soil layers/horizons and soil hydraulic parameters
