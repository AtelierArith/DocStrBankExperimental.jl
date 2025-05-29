```
plotisotopes(simulation::DiscretizedSPAC)
plotisotopes(simulation::DiscretizedSPAC, isotope::Symbol)
plotisotopes(simulation::DiscretizedSPAC, isotope::Symbol, (d18O = (-6, -16), d2H = (-125, -40)))
plotisotopes(simulation::DiscretizedSPAC, isotope::Symbol, (d18O = (-6, -16), d2H = (-125, -40)), RWUcentroid::Symbol))
```

Plots the isotope results of a SPAC Simulation. By default both δ18O and δ2H. The user can override this with the second argument isotope as one of `:d18O`, `:d2H`, or `:d18O_and_d2H`. RWUcentroid can have values of either `:dontShowRWUcentroid` or `:showRWUcentroid`.
