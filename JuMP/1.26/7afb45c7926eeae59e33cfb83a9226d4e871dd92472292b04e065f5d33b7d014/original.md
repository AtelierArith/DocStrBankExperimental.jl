```
copy_model(model::GenericModel; filter_constraints::Union{Nothing, Function}=nothing)
```

Return a copy of the model `model` and a [`GenericReferenceMap`](@ref) that can be used to obtain the variable and constraint reference of the new model corresponding to a given `model`'s reference. A [`Base.copy(::AbstractModel)`](@ref) method has also been implemented, it is similar to `copy_model` but does not return the reference map.

If the `filter_constraints` argument is given, only the constraints for which this function returns `true` will be copied. This function is given a constraint reference as argument.

## Note

Model copy is not supported in `DIRECT` mode, that is, when a model is constructed using the [`direct_model`](@ref) constructor instead of the [`Model`](@ref) constructor. Moreover, independently on whether an optimizer was provided at model construction, the new model will have no optimizer, that is, an optimizer will have to be provided to the new model in the [`optimize!`](@ref) call.

## Example

In the following example, a model `model` is constructed with a variable `x` and a constraint `cref`. It is then copied into a model `new_model` with the new references assigned to `x_new` and `cref_new`.

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @constraint(model, cref, x == 2)
cref : x = 2

julia> new_model, reference_map = copy_model(model);

julia> x_new = reference_map[x]
x

julia> cref_new = reference_map[cref]
cref : x = 2
```
