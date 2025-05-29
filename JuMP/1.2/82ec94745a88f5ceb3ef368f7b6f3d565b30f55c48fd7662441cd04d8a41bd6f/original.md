```
copy_extension_data(data, new_model::AbstractModel, model::AbstractModel)
```

Return a copy of the extension data `data` of the model `model` to the extension data of the new model `new_model`.

A method should be added for any JuMP extension storing data in the `ext` field.

!!! warning
    Do not engage in type piracy by implementing this method for types of `data` that you did not define! JuMP extensions should store types that they define in `model.ext`, rather than regular Julia types.

