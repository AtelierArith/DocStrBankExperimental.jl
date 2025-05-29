**ON GRID**

```
gmpe_simidorikawa1999(
    eq::Earthquake,config::Params_simidorikawa1999,
    grid::Array{Point_vs30};
    min_val::Number
)
```

where `min_val=0` by default

Output will be 1-d `Array{Point_pga_out}` with points based on the input grid with `pga > min_val` (pga is Acceleration of gravity in percent (%g) rounded to ggg.gg)

**without grid**

```
gmpe_simidorikawa1999(
    eq::Earthquake,
    config::Params_simidorikawa1999;
    VS30::Number=350,
    distance::Int64=1000
)
```

where `VS30=30` [m/s^2], `distance=1000` [km] by default.

Output will be 1-d `Array{Float64,1}` with `1:distance` values of `pga` (that is Acceleration of gravity (g) in percent rounded to ggg.gg)

**EXAMPLES:**

```
gmpe_simidorikawa1999(
    eq,config_simidorikawa1999_interplate,grid
) # for PGA on GRID

gmpe_simidorikawa1999(
    eq,config_simidorikawa1999_intraplate
) # for PGA without input grid
```

**Model parameters**

Please, see `examples/si-midorikawa-1999.conf`
