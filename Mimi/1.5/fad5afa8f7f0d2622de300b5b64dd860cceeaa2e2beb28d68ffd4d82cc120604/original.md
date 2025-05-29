```
set_leftover_params!(md::ModelDef, parameters::Dict)
```

Set all of the parameters in `ModelDef` `md` that don't have a value and are not connected to some other component to a value from a dictionary `parameters`. This method assumes the dictionary keys are Symbols (or convertible into Symbols ie. Strings) that  match the names of unset parameters in the model. All resulting connected model  parameters will be shared model parameters.

Note that this function `set_leftover_params! has been deprecated, and uses should be transitioned to using`update*leftover*params!` with keys specific to component-parameter  pairs i.e. (comp*name, param*name) => value in the dictionary.
