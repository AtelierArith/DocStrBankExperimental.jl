```
getSignalNames(instantiatedModel::Modia.InstantiatedModel;
               getVar=true, getPar=true, getMap=true)::Vector{String}
```

Returns a string vector of the variables of an [`@instantiateModel`](@ref) that are present in the result or are (evaluated) parameters.

  * If getVar=true, Var(..) variables are included.
  * If getPar=true, Par(..) variables are included.
  * If getMap=true, Map(..) variables are included.
