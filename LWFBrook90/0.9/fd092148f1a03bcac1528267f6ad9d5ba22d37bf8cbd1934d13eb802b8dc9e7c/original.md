```
get_fluxes(simulation::DiscretizedSPAC; days_to_read_out_d = nothing)
```

Returns a DataFrame with amounts (and isotopoic compositions) of the ecosystem water fluxes*.

By default, the values are returned for each simulation day. The user can optionally define timestep using the input argument `days_to_read_out_d` as:

  * a numeric vector, e.g. `days_to_read_out_d = 1:1.0:100` for specific days since `simulation.parametrizedSPAC.reference_date`

Subsets of scalar state variables or soil states can be mad afterwards with:

```
simout_fluxes = get_fluxes(simulation)
simout_fluxes[:, Not(r"[0-9]mm$")]    # select only scalar fluxes (by de-selecting columns containing depth information e.g. "_150mm")
simout_fluxes[:, r"(dates)|([0-9]mm)"] # select only vector fluxes (by selecting columns containing depth information e.g. "_150mm")
```

* fluxes returned as columns in the DataFrame are:

```
:dates

:cum_d_prec,:cum_d_sfal,:cum_d_sthr,:cum_d_sint,
:cum_d_rfal,:cum_d_rint,:cum_d_rthr,:cum_d_rsno,:cum_d_rnet,:cum_d_smlt,
:cum_d_irvp,:cum_d_isvp,:cum_d_snvp,:cum_d_slvp,
:cum_d_tran,
:cum_d_pint, :cum_d_ptran, :cum_d_pslvp,
:srfl,:slfl,:byfl,:dsfl,:gwfl,:vrfln,

:flow, :seep, :evap,

:TRANI_mmday_50mm, :TRANI_mmday_100mm, ... :TRANI_mmday_1050mm, :TRANI_mmday_1100mm
```

Returns:

```
366×50 DataFrame
 Row │ dates                cum_d_prec  cum_d_sfal  cum_d_sthr  cum_d_sint  cum_d_rfal  cum_d_rint  cum_d_rthr  cum_d_rsno  cum_d_rnet  cum_d_smlt   ⋯
     │ DateTime             Float64     Float64     Float64     Float64     Float64     Float64     Float64     Float64     Float64     Float64      ⋯
─────┼────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────── ─
   1 │ 2021-01-01T00:00:00         0.0    0.0         0.0        0.0          0.0         0.0         0.0         0.0          0.0         0.0       ⋯
   2 │ 2021-01-02T00:00:00         0.0    0.0         0.0        0.0          0.0         0.0         0.0         0.0          0.0         0.0       ⋯

     ⋯ cum_d_irvp  cum_d_isvp  cum_d_snvp  cum_d_slvp  cum_d_tran   cum_d_pint  cum_d_ptran  cum_d_pslvp  srfl     slfl      byfl     dsfl      ⋯
     ⋯ Float64     Float64     Float64     Float64     Float64      Float64     Float64      Float64      Float64  Float64   Float64  Float64   ⋯
     ────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
     ⋯   0.0        0.0         0.0        0.0         0.0            0.0       0.0            0.0            0.0   0.0          0.0      0.0   ⋯
     ⋯   0.0        0.0         0.0        0.0448292   0.0566162      2.64652   0.0566162      0.364727       0.0   0.0          0.0      0.0   ⋯

     ⋯ gwfl      vrfln     flow      seep     evap       TRANI_mmday_50mm  TRANI_mmday_100mm  TRANI_mmday_150mm  TRANI_mmday_200mm  TRANI_mmday_250mm  ⋯ TRANI_mmday_1050mm TRANI_mmday_1100mm
     ⋯ Float64   Float64   Float64   Float64  Float64    Float64           Float64            Float64            Float64            Float64            ⋯ Float64            Float64
     ────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
     ⋯ 0.0       0.0       0.0           0.0  0.0             0.0                0.0                0.0                0.0                0.0          ⋯                0.0               0.0
     ⋯ 0.154122  0.154122  0.154122      0.0  0.101445        0.0434988          0.00995972         0.00240976         0.000574825        0.00013463   ⋯                0.0               0.0
```
