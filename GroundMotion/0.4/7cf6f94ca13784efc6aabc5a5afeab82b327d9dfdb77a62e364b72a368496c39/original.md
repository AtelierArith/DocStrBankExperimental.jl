**ON GRID**

```
gmpe_as2008(
    eq::Earthquake,
    config_as2008::Params_as2008,
    grid::Array{Point_vs30};
    min_val::Number
)
```

where `min_val=0` by default

Output will be 1-d `Array{Point_pga_out}` with points based on input grid with `pga > min_val` (pga, is Acceleration of gravity in percent (%g) rounded to ggg.gg)

**without grid**

```
gmpe_as2008(
    eq::Earthquake,
    config::Params_as2008,
    VS30::Number=350,
    distance::Int64=1000
)
```

where `VS30=30` [m/s^2], `distance=1000` [km] by default.

Output will be 1-d `Array{Float64}` with `1:distance` values of `pga` (that is Acceleration of gravity in percent (%g) rounded to ggg.gg)

**EXAMPLES:**

```
gmpe_as2008(eq,config_as2008,grid) # for PGA on GRID
gmpe_as2008(eq,config_as2008) # for without input grid
```

**Model parameters**

Please, see `examples/as-2008.conf`
