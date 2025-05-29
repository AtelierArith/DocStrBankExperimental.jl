**ON GRID**

  * On grid without Dl data:

```
gmpe_mf2013(
    eq::Earthquake,
    config::Params_mf2013,
    grid::Array{Point_vs30};
    min_val::Number=0,
    Dl::Number=250,
    Xvf::Number=0
)
```

  * On grid with Dl data

```
gmpe_mf2013(
    eq::Earthquake,
    config::Params_mf2013,
    grid::Array{Point_vs30_dl};
    min_val::Number=0,
    Xvf::Number=0
)
```

where `min_val=0`, `Xvf=0` [km] by default. `Dl=250` [km] by default in case of grid pass without `Dl` data.

Output will be 1-d `Array{Point_<ground_motion_type>_out}` with points based on input grid with `ground_motion > min_val` (`pga`,`psa` is Acceleration of gravity in percent (%g) rounded to ggg.gg, `pgv` in cm/s^2)

**Without grid**

```
gmpe_as2008(
    eq::Earthquake,
    config::Params_mf2013;
    VS30::Number=350,
    distance::Int64=1000,
    Dl::Number=250,
    Xvf::Number=0
)
```

where `VS30=30` [m/s^2], `distance=1000` [km], `Xvf=0` [km], `Dl=250` [km] by default.

Output will be 1-d `Array{Float64}` with `1:distance` values of `pga`,`psa` (that is Acceleration of gravity in percent (%g) rounded to ggg.gg) OR pgv [cm/s].

**EXAMPLES:**

```
gmpe_mf2013(
    eq,
    config_mf2013,
    grid
) # for PGA,PGV,PSA on GRID

gmpe_mf2013(
    eq,
    config_mf2013
) # for PGA,PGV,PSA without input grid
```

**Model parameters**

Please, see `examples/morikawa-fujiwara-2013.conf`
