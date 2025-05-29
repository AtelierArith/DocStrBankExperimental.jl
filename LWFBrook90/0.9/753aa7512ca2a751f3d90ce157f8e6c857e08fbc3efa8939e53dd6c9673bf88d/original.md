```
loadSPAC(folder::String, prefix::String;
        # OPTIONAL ARGUMENTS ARE:
        simulate_isotopes::Bool = true,
        canopy_evolution  = "meteoveg.csv",
        Δz_thickness_m    = "soil_discretization.csv",
        root_distribution = "soil_discretization.csv",
        IC_soil           = "soil_discretization.csv",
        IC_scalar         = "initial_conditions.csv",
        storm_durations_h = "meteo_storm_durations.csv")
```

Create instance of SPAC model by loading different input files for LWFBrook90 from folder `folder`` with the names:

  * `[PREFIX]_meteoveg.csv`
  * `[PREFIX]_meteo_iso.csv` (needed for isotopic)
  * `[PREFIX]_param.csv`
  * `[PREFIX]_meteo_storm_durations.csv`
  * `[PREFIX]_initial_conditions.csv`
  * `[PREFIX]_soil_horizons.csv`

These files were created with an R script `generate_LWFBrook90jl_Input.R` that takes the same arguements as the R function `LWFBrook90R::run_LWFB90()` and generates the corresponding input files for LWFBrook90.jl.

Soil discretization can be provided as vector with the thickness of each cell, e.g: `Δz_thickness_m = fill(0.04, 20)`.

Root distribution can be provided as arguments to function `Rootden_()` as  `(beta = 0.98, )` or `(beta = 0.98, z_rootMax_m=-0.5)` or for the gamma distribution `(root_k = 1.0, root_θ_cm = 20.0, z_rootMax_m=-0.5)`.

Meteo storm durations can be provided as vector for each month, e.g.: `[4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4, 4]`

Initial conditions in the soil can be provided as NamedTuple `IC_soil = (PSIM_init_kPa = -7.0, delta18O_init_permil = -9.0, delta2H_init_permil = -11.0)`

Canopy evolution can be provided as NamedTuple, giving the constant values of DENSEF, HEIGHT, SAI and dynamic evolution of LAI:

```
canopy_evolution = (DENSEF_rel = 100,
                    HEIGHT_rel = 100,
                    SAI_rel    = 100,
                    LAI_rel = (DOY_Bstart = 120,
                            Bduration  = 21,
                            DOY_Cstart = 270,
                            Cduration  = 60,
                            LAI_perc_BtoC = 100,
                            LAI_perc_CtoB = 20))
```

The vegetation season in terms of LAI is defined by defining the year into 4 parts: A->B, B->B+, B+->C, C->C+, C+->A where A is the start of the year (January 1st). effectively giving the 4 parts: C+->B, B->B+, B+->C, C->C+. The position and durationof these periods are defined in days by parameters: DOY_Bstart, Bduration, DOY_Cstart, and Cduration. LAI (in percent) is constant from C+->B and B+->C (given by LAI_perc_CtoB and LAI_perc_BtoC) and a simple linear interpolation is done for in_between (i.e. budburst and leaffall).

Initial conditions of states other than soil can be provided as NamedTuple, e.g.:

```
IC_scalar = (amount = (u_GWAT_init_mm = 0,
                       u_INTS_init_mm = 0,
                       u_INTR_init_mm = 0,
                       u_SNOW_init_mm = 0,
                       u_CC_init_MJ_per_m2 = 0,
                       u_SNOWLQ_init_mm =  0),
            d18O    = (u_GWAT_init_permil = -13.,
                       u_INTS_init_permil = -13.,
                       u_INTR_init_permil = -13.,
                       u_SNOW_init_permil = -13.),
            d2H     = (u_GWAT_init_permil = -95.,
                       u_INTS_init_permil = -95.,
                       u_INTR_init_permil = -95.,
                       u_SNOW_init_permil = -95.))
```
