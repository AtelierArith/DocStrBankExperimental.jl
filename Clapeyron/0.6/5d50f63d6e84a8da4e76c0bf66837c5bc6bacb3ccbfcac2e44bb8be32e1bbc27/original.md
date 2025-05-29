```
UNIFACFVModel <: ActivityModel

UNIFACFV(components;
puremodel = PR,
userlocations = String[],
group_userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## Input parameters

  * `volume`: Single Parameter (`Float64`)  - specific volume of species `[g/cm^3]`
  * `R`: Single Parameter (`Float64`)  - Normalized group Van der Vals volume
  * `Q`: Single Parameter (`Float64`) - Normalized group Surface Area
  * `A`: Pair Parameter (`Float64`, asymetrical, defaults to `0`) - Binary group Interaction Energy Parameter
  * `Mw`: Single Parameter (`Float64`) - Molecular weight of groups

## Input models

  * `puremodel`: model to calculate pure pressure-dependent properties

## Description

UNIFACFV (UNIFAC Free Volume) activity model. specialized for solvent-polymer mixtures

The Combinatorial part corresponds to an GC-averaged modified [`UNIQUAC`](@ref) model.

```
Gᴱ = nRT(gᴱ(comb) + gᴱ(res) + gᴱ(FV))
```

## References
