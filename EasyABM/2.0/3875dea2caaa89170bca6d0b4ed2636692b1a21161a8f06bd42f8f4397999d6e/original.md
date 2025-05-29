```julia
get_patch_data(
    patch,
    model::EasyABM.AbstractSpaceModel
) -> Union{Nothing, @NamedTuple{record::DataFrames.DataFrame}}
get_patch_data(
    patch,
    model::EasyABM.AbstractSpaceModel,
    props
) -> Union{Nothing, @NamedTuple{record::DataFrames.DataFrame}}

```
