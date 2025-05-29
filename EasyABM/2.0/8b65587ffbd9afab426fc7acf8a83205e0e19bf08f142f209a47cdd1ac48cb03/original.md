```julia
get_model_data(
    model::Union{EasyABM.AbstractGraphModel, EasyABM.AbstractSpaceModel}
) -> @NamedTuple{record::DataFrames.DataFrame}
get_model_data(
    model::Union{EasyABM.AbstractGraphModel, EasyABM.AbstractSpaceModel},
    props
) -> @NamedTuple{record::DataFrames.DataFrame}

```
