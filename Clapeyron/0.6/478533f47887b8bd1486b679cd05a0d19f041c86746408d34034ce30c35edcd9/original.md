```
split_model(model::EoSModel)
split_model(model::EoSModel, splitter)
```

Takes in a model for a multi-component system and returns a vector of models. The result depends on the splitter used.

A model can be splitted in a list of submodels, where each submodel is of the same type as the original model, but it has a different combination of components.

Group-Contribution models are also splitted in a component basis, `split_model` takes care of converting between Group and Component basis automatically.

A splitter is just a list of indices for each submodel, valid splitters are:

  * A list of integers: `split_model(model,[1,5,2])` will return three pure models.
  * An integer: `split_model(model,1)` will return a list with one model corresponding to the first component
  * A list of lists: `split_model(model,[[1,2],[3])` will return a list with two models, the first one will contain two components, the second one will be a pure model.

The default splitter is `1:length(model)`, that will return a list with all pure models.

## Examples

```julia-repl
julia> model = MonomerIdeal(["methane","propane","butane"])
MonomerIdeal with 3 components:
 "methane"
 "propane"
 "butane"
Contains parameters: Mw, reference_state

julia> split_model(model)
3-element Vector{MonomerIdeal}:
 MonomerIdeal("methane")
 MonomerIdeal("propane")
 MonomerIdeal("butane")
 
julia> split_model(model,[[1,2],[3,1]])
2-element Vector{MonomerIdeal}:
 MonomerIdeal("methane", "propane")
 MonomerIdeal("butane", "methane")

julia> split_model(model,2)
1-element Vector{MonomerIdeal}:
 MonomerIdeal("propane")
```
