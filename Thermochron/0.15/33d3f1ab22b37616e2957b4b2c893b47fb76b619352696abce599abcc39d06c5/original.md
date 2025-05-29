```julia
modellength(track::ApatiteTrackLength, Tsteps, am::ApatiteAnnealingModel)
```

Calculate the predicted mean and standard deviation of the distribution of fission   track lengths of an apatite that has experienced a given t-T path (specified by  `track.tsteps` for time and `Tsteps` for temperature, at a time resolution of  `step(mineral.tsteps)`) and given annealing model parameters `am`.

Possible annealing model types and the references for the equations  which they respetively implement include    `Ketcham1999FC`       Fanning Curvilinear apatite model of Ketcham et al. 1999 (doi: 10.2138/am-1999-0903)   `Ketcham2007FC`       Fanning Curvilinear apatite model of Ketcham et al. 2007 (doi: 10.2138/am.2007.2281)
