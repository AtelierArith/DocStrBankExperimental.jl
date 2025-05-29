```
HANNA <: ActivityModel
HANNA(components;
puremodel = nothing,
userlocations = String[],
pure_userlocations = String[],
verbose = false,
reference_state = nothing)
```

## Input parameters

  * `canonicalsmiles`: canonical SMILES (using RDKit) representation of the components
  * `Mw`: Single Parameter (`Float64`) (Optional) - Molecular Weight `[g/mol]`

## Input models

  * `puremodel`: model to calculate pure pressure-dependent properties

## Description

Hard-Constraint Neural Network for Consistent Activity Coefficient Prediction (HANNA v1.0.0). The implementation is based on [this](https://github.com/tspecht93/HANNA) Github repository. HANNA was trained on all available binary VLE data (up to 10 bar) and limiting activity coefficients from the Dortmund Data Bank. HANNA was only tested for binary mixtures so far. The extension to multicomponent mixtures is experimental.

To use the model, the package `ClapeyronHANNA` must be installed and loaded (see example below).

## Example

```julia
using Clapeyron, ClapeyronHANNA

components = ["water","isobutanol"]
Mw = [18.01528, 74.1216]
smiles = ["O", "CC(C)CO"]

model = HANNA(components,userlocations=(;Mw=Mw, canonicalsmiles=smiles))
# model = HANNA(components) # also works if components are in the database 
```

## References

1. Specht, T., Nagda, M., Fellenz, S., Mandt, S., Hasse, H., Jirasek, F., HANNA: Hard-Constraint Neural Network for Consistent Activity Coefficient Prediction. Chemical Science 2024. [10.1039/D4SC05115G](https://doi.org/10.1039/D4SC05115G).
