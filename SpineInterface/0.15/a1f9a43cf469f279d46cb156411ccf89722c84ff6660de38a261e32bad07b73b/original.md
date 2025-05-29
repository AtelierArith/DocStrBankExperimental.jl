```
write_parameters(parameters, url::String; <keyword arguments>)
```

Write `parameters` to the Spine database at the given RFC-1738 `url`. `parameters` is a dictionary mapping parameter names to another dictionary mapping object or relationship (`NamedTuple`) to values.

# Arguments

  * `parameters::Dict`: a dictionary mapping parameter names, to entities, to parameter values
  * `upgrade::Bool=true`: whether or not the database at `url` should be upgraded to the latest revision.
  * `for_object::Bool=true`: whether to write an object parameter or a 1D relationship parameter in case the number of dimensions is 1.
  * `report::String=""`: the name of a report object that will be added as an extra dimension to the written parameters.
  * `alternative::String`: an alternative where to write the parameter values.
  * `comment::String=""`: a comment explaining the nature of the writing operation.
