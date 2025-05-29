```
MonomerIdeal <: MonomerIdealModel

MonomerIdeal(components; 
userlocations = String[],
reference_state = nothing,
verbose = false)
```

## Input parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`

## Model Parameters

None

## Description

Monomer Ideal Model, result obtained from statistical mechanics `Λ`

```
    Λᵢ = h/√(kᵦTMwᵢ/Nₐ)    
    a₀ = A₀/nRT = ∑xᵢlog(ρᵢΛᵢ^3)
```

## Model Construction Examples

```
# Using the default database
idealmodel = MonomerIdeal("water") #single input
idealmodel = MonomerIdeal(["water","ethanol"]) #multiple components

# Using user-provided parameters

# Passing files or folders
idealmodel = MonomerIdeal(["neon","hydrogen"]; userlocations = ["path/to/my/db","mw.csv"])

# Passing parameters directly
idealmodel = MonomerIdeal(["neon","hydrogen"];userlocations = (;Mw = [20.17, 2.]))
```
