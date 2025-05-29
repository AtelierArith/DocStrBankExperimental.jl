```
PALEOboxes
```

PALEOboxes provides the model coupler for the PALEO model framework.

It is registered as a Julia package with public github repository [PALEOboxes.jl](https://github.com/PALEOtoolkit/PALEOboxes.jl)  and online  [documentation](https://paleotoolkit.github.io/PALEOboxes.jl)

A PALEO `Model` contains `Domain`s, each of which contain Variables  defining `Field`s containing `Data` arrays, and Reactions with `ReactionMethod`s that operate on the Variables to calculate model time evolution.

PALEOboxes creates the model from a .yaml configuration file, and implements a coupler that provides  a unified mechanism for:

1. ‘low-level’ coupling (e.g. linking individual redox Reactions within a Domain, on which is built
2. ‘module-level’ coupling (linking e.g. atmosphere and ocean components) based on standardising names for communicating fluxes, and which enables
3. separation of biogeochemical reaction and transport.
