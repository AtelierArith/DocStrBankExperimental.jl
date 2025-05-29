```
 prescribed_analytic_forcing(FT = Float32;
                             earth_param_set = LP.LandParameters(FT),
                             start_date = DateTime(2005),
                             SW_d = (t) -> 0,
                             LW_d = (t) -> 5.67e-8 * 280.0^4.0,
                             precip = (t) -> 0, # no precipitation
                             T_atmos = (t) -> 280.0,
                             u_atmos = (t) -> 1.0,
                             q_atmos = (t) -> 0.0, # no atmos water
                             h_atmos = FT(1e-8),
                             P_atmos = (t) -> 101325,
                             atmos = PrescribedAtmosphere(
                                 TimeVaryingInput(precip),
                                 TimeVaryingInput(precip),
                                 TimeVaryingInput(T_atmos),
                                 TimeVaryingInput(u_atmos),
                                 TimeVaryingInput(q_atmos),
                                 TimeVaryingInput(P_atmos),
                                 start_date,
                                 h_atmos,
                                 earth_param_set,
                             ),
                             radiation = PrescribedRadiativeFluxes(
                                 FT,
                                 TimeVaryingInput(SW_d),
                                 TimeVaryingInput(LW_d),
                                 start_date,
                             ),
                         )
```

A helper function which constructs the `PrescribedAtmosphere` and `PrescribedRadiativeFluxes` for a simple analytic case.
