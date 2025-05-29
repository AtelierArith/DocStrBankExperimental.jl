```
@replaceparameterlinks model oldmodel => newmodel
```

This function is used when a model uses parameters which link to another model object. The function must be called with a pair of models as they appear in the Main module.

This is useful when ones models are modularized and include sattelite models. The function can then be used to link the parameters in modified copies of the sattelite model to modified  copies of the main model. For example, if the FRBUS_VAR model has a main model and a sattelite model the following workflow would make sense.

```
using FRBUS_VAR
m = deepcopy(FRBUS_VAR.model)
m_sattelite = deepcopy(FRBUS_VAR.sattelitemodel)

## INSERT CHANGES to m
@reinitialize m
@replaceparameterlinks m_sattelite FRBUS_VAR.model => m
@reinitialize m_sattelite

```

Changes like this should be followed by a call to [`@reinitialize`](@ref) on the model.
