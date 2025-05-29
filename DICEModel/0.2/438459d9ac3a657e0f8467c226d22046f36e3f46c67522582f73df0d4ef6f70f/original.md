```
DICEParameters
```

Row and computed parameters for the optimization function.

This structure contains the "default of the default" parameters, which can eventually be modified using either keyword arguments in specific functions (each defining its own "defaults") or directly in the `run_dice(pars)` function (e.g. `run_dice(a2base = [0.01])`). This second method overrides the specific defaults of the `DICE2013` function.

The structure first defines some "raw" parameters, and then some "computed" parameters (mostly matrices of ntsteps x nregions length). Both can be overridden with keyword arguments. In particular, "computed" parameters can be overridden in two ways: either by overriding the raw parameters from which they are computed, or by computing the parameter in a different way (outside the model) and overriding the computed parameter.

# Available parameters:

  * `tstep`: Years per period
  * `ntsteps`: Number of time periods
  * `regions`: Name of the regions
  * `weights`: Utility weights to assign to each region. Note these are **exogenous** (default to equal weights), are NOT the Negishi weights.
  * `gamma`: Capital elasticity in production function
  * `pop1`: Initial world population 2020 (millions)
  * `popadj`: Growth rate to calibrate to 2050 population projection
  * `popasym`: Asymptotic population (millions)
  * `dk`: Depreciation rate on capital (per year)
  * `q1`: Initial world output 2020 (trill 2019 USD)
  * `al1`: Initial level of total factor productivity
  * `ga1`: Initial growth rate for TFP per 5 years
  * `dela`: Decline rate of TFP per 5 years
  * `gsigma1`: Initial growth of sigma (per year)
  * `delgsig`: Decline rate of gsigma per period
  * `asymgsig`: Asymptotic sigma
  * `e1`: Industrial emissions 2020 (GtCO2 per year)
  * `miu1`: Emissions control rate historical 2020
  * `cumemiss0`: Cumulative emissions 2020 (GtC)
  * `a1`: Damage intercept
  * `a2base`: Damage quadratic term
  * `a3`: Damage exponent
  * `expcost2`: Exponent of control cost function
  * `pback2050`: Cost of backstop in 2019$ per tCO2 (2050)
  * `limmiu2070`: Emission control limit from 2070
  * `limmiu2120`: Emission control limit from 2120
  * `limmiu2200`: Emission control limit from 2220
  * `limmiu2300`: Emission control limit from 2300
  * `delmiumax`: Emission control delta limit per period
  * `betaclim`: Climate beta
  * `elasmu`: Elasticity of marginal utility of consumption
  * `prstp`: Pure rate of social time preference
  * `pi_val`: Capital risk premium (renamed to avoid conflict with Julia's pi)
  * `k0`: Initial capital stock (10^12 2019 USD)
  * `siggc1`: Annual standard deviation of consumption growth
  * `srf`: Scaling factor for discounting
  * `scale1`: Multiplicative scaling coefficient
  * `scale2`: Additive scaling coefficient
  * `eland0`: Carbon emissions from land 2015 (GtCO2 per year)
  * `deland`: Decline rate of land emissions (per period)
  * `f_misc2020`: Non-abatable forcings 2020
  * `f_misc2100`: Non-abatable forcings 2100
  * `f_ghgabate2020`: Forcings of abatable non-CO2 GHG in 2020
  * `eco2eghgb2020`: Emissions of abatable non-CO2 GHG (GtCO2e) in 2020
  * `eco2eghgb2100`: Emissions of abatable non-CO2 GHG (GtCO2e) in 2100
  * `emissrat2020`: Ratio of CO2e to industrial CO2 in 2020
  * `emissrat2100`: Ratio of CO2e to industrial CO2 in 2100
  * `fcoef1`: Coefficient of non-CO2 abateable emissions
  * `fcoef2`: Coefficient of non-CO2 abateable emissions
  * `yr0`: Calendar year that corresponds to model year zero
  * `emshare0`: Carbon emissions share into Reservoir 0
  * `emshare1`: Carbon emissions share into Reservoir 1
  * `emshare2`: Carbon emissions share into Reservoir 2
  * `emshare3`: Carbon emissions share into Reservoir 3
  * `tau0`: Decay time constant for Reservoir 0
  * `tau1`: Decay time constant for Reservoir 1
  * `tau2`: Decay time constant for Reservoir 2
  * `tau3`: Decay time constant for Reservoir 3
  * `teq1`: Thermal equilibration parameter for box 1
  * `teq2`: Thermal equilibration parameter for box 2
  * `d1`: Thermal response timescale for deep ocean
  * `d2`: Thermal response timescale for upper ocean
  * `irf0`: Pre-industrial IRF100
  * `irc`: Increase in IRF100 with cumulative carbon uptake
  * `irt`: Increase in IRF100 with warming
  * `fco22x`: Forcings of equilibrium CO2 doubling
  * `mat0`: Initial concentration in atmosphere in 2020 (GtC)
  * `res00`: Initial concentration in Reservoir 0 in 2020 (GtC)
  * `res10`: Initial concentration in Reservoir 1 in 2020 (GtC)
  * `res20`: Initial concentration in Reservoir 2 in 2020 (GtC)
  * `res30`: Initial concentration in Reservoir 3 in 2020 (GtC)
  * `mateq`: Equilibrium concentration in atmosphere (GtC)
  * `tbox10`: Initial temperature box 1 change in 2020 (°C)
  * `tbox20`: Initial temperature box 2 change in 2020 (°C)
  * `tatm0`: Initial atmospheric temperature change in 2020 (°C)
  * `times`: Time periods sequence (0,5,10,...,400)
  * `tidx`: Time periods index sequence (1,2,3,...,81)
  * `t0idx`: Time periods index sequence (0,1,2,...,80)
  * `nreg`: Number of regions
  * `ridx`: Regions index sequence
  * `rartp`: Risk-adjusted rate of time preference
  * `miuup`: Upper bounds on miu
  * `varpcc`: Variance of per capita consumption
  * `rprecaut`: Precautionary rate of return
  * `rr1`: STP factor without precautionary factor
  * `rr`: STP with precautionary factor
  * `optlrsav`: Optimal long-run savings rate used for transversality
  * `l_temp`: Level of population and labor (temp, used only for its first value)
  * `l`: Level of population and labor
  * `ga`: Growth rate of Total Factor Productivity
  * `al_temp`: Level of total factor productivity (temp, used only for its first value)
  * `al`: Level of total factor productivity
  * `pbacktime`: Backstop price 2019$ per ton CO2
  * `sig1`: Carbon intensity 2020 kgCO2-output 2020
  * `gsig`: Change in sigma (rate of decarbonization)
  * `sigma_temp`: CO2-emissions output ratio (temp, used only for its first value)
  * `sigma`: CO2-emissions output ratio
  * `eland`
  * `co2e_ghgabateb`
  * `f_misc`
  * `emissrat`
  * `sigmatot`
  * `cost1tot`
