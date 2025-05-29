```
@newmodelgc modelname parent paramstype [sitemodel = true, use_struct_param = false]
```

This is a data type that contains all the information needed to use an EoS model. It also functions as an identifier to ensure that the right functions are called.

You can pass an optional 4th `Bool` argument  indicating if you want to use sites with this model or not. defaults to `true`

You can also pass another optional 5th `Bool` argument indicating if a second order GroupParam (`StructGroupParam`) is used or not. defaults to `false`

= Fields = The Struct consists of the following fields:

  * components: a string lists of components
  * groups: a [`GroupParam`](@ref)
  * sites: a [`SiteParam`](@ref) (optional)
  * params: the Struct paramstype that contains all parameters in the model
  * idealmodel: the IdealModel struct that determines which ideal model to use
  * assoc_options: struct containing options for the association solver. see [`AssocOptions`](@ref)
  * references: reference for this EoS

See the tutorial or browse the implementations to see how this is used.
