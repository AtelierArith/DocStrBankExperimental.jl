```julia
simulate!(
    model,
    clock;
    simdir,
    simprefix,
    simname,
    logtofile,
    loglevel,
    reportsim,
    withbar,
    breakpoints
)

```

Simulates `model`. `simdir` is the path of the directory into which simulation files are saved. `simprefix` is the prefix of the simulation name `simname`. If `logtofile` is `true`, a log file for the simulation is constructed. `loglevel` determines the logging level. If `reportsim` is `true`, model components are saved into files. If `withbar` is `true`, a progress bar indicating the simualation status is displayed on the console.
