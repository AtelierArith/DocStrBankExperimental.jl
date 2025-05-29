```
InterpretMe.partial_dependence(data::Array{<:Any,2},
                               features::Union{<:Integer,Vector{<:Integer}},
                               estimate_fn, grid_size::Int,
                               return_ice::Bool)
```

Calculate the partial dependance of a machine learning model.

`estimate_fn` is a function from the model that generates a vector of predictions from a matrix of inputs. `feature_names` should be the feature names corresponding to the features in `data` `return_ice` whether to return the ICE lines. Returns `pd` the partial dependancy results `grid_values` the grid values for all the selected features 
