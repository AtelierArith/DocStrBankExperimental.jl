```
get_states(simulation::DiscretizedSPAC; days_to_read_out_d = nothing)
```

Returns a DataFrame with amounts (and isotopoic compositions) of the inputs and state variables: PREC, GWAT, INTS, INTR, SNOW, (amount only: CC, SNOWLQ), (signature only: XYLEM). RWU flux can be obtained with `get_fluxes()`. By default, the values are returned for each simulation day. The user can optionally define timestep using the input argument `days_to_read_out_d` as:

  * `:integrator_step` to have it each simulation time step
  * a numeric vector, e.g. `days_to_read_out_d = 1:1.0:100` for specific days since `simulation.parametrizedSPAC.reference_date`

Subsets of scalar state variables or soil states can be mad afterwards with:

```
simout_states = get_states(simulation)
simout_states[:, Not(r"[0-9]mm$")]    # select only scalar states (by de-selecting columns containing depth information e.g. "_150mm")
simout_states[:, r"(dates)|([0-9]mm)"] # select only vector states (by selecting columns containing depth information e.g. "_150mm")
```

Returns:

```
366×108 DataFrame
 Row │ dates                GWAT_mm  INTS_mm   INTR_mm       SNOW_mm  CC_MJm2     SNOWLQ_mm  SWAT_mm  GWAT_d18O  INTS_d18O  INTR_d18O  SNOW_d18O  XYLEM_d18O  ⋯ δ18O_permil_50mm  δ18O_permil_100mm  δ18O_permil_1 ⋯ ψ_kPa_1100mm
     │ DateTime             Float64  Float64   Float64       Float64  Float64     Float64    Float64  Float64    Float64    Float64    Float64    Float64     ⋯ Float64           Float64            Float64       ⋯ Float 64
─────┼──────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
   1 │ 2021-01-01T00:00:00      1.0  0.0        0.0           0.0     0.0          0.0       90.2641  -13.0        -13.0      -13.0      -13.0     -10.1111  ⋯         -10.1111           -10.1111           -10. ⋯ -7
   2 │ 2021-01-02T00:00:00      1.0  0.0        0.0           0.0     0.0          0.0       90.4532  -12.5973     -15.04     -15.04     -15.04    -10.1111            -10.1111           -10.1111           -10. ⋯ -6.43
```
