```julia
modelage(mineral::ZirconFT, Tsteps, am::ZirconAnnealingModel)
modelage(mineral::MonaziteFT, Tsteps, am::MonaziteAnnealingModel)
modelage(mineral::ApatiteFT, Tsteps, am::ApatiteAnnealingModel)
```

Calculate the precdicted fission track age of an apatite that has experienced a given  t-T path (specified by `mineral.tsteps` for time and `Tsteps` for temperature, at a time resolution of `step(mineral.tsteps)`) and given annealing model parameters `am`.

Possible annealing model types and the references for the equations  which they respetively implement include    `Ketcham1999FC`       Fanning Curvilinear apatite model of Ketcham et al. 1999 (doi: 10.2138/am-1999-0903)   `Ketcham2007FC`       Fanning Curvilinear apatite model of Ketcham et al. 2007 (doi: 10.2138/am.2007.2281)   `Yamada2007PC`        Parallel Curvilinear zircon model of Yamada et al. 2007 (doi: 10.1016/j.chemgeo.2006.09.002)   `Guenthner2013FC`     Fanning Curvilinear zircon model of Guenthner et al. 2013 (doi: 10.2475/03.2013.01)   `Jones2021FA`         Fanning Arrhenius (Fanning Linear) model adapted from Jones et al. 2021 (doi: 10.5194/gchron-3-89-2021)
