```
load_model(data, r, rmean, fittedparam, fixedeffects, transitions, G, R, S, insertstep, splicetype, nalleles, priorcv, onstates, decayrate, propcv, probfn, noisepriors, method, hierarchical, coupling, grid, zeromedian, ejectnumber, factor)
```

Construct and return the appropriate model struct for the given data and options.

# Arguments

  * `data`: Data structure.
  * `r`, `rmean`, `fittedparam`, `fixedeffects`, `transitions`, `G`, `R`, `S`, `insertstep`, `splicetype`, `nalleles`, `priorcv`, `onstates`, `decayrate`, `propcv`, `probfn`, `noisepriors`, `method`, `hierarchical`, `coupling`, `grid`, `zeromedian`, `ejectnumber`, `factor`: Model options.

# Returns

  * Model struct (e.g., `GMmodel`, `GRSMmodel`).
