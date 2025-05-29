```julia
timelogger(
;
    showiter,
    showt,
    showdt,
    showmax,
    showspeed,
    nupdate
) -> @NamedTuple{initialize::IncompressibleNavierStokes.var"#286#288"{Bool, Bool, Bool, Bool, Bool, Int64}, finalize::IncompressibleNavierStokes.var"#283#284"}

```

Create processor that logs time step information.
