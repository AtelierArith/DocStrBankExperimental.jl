```
optimizer_with_attributes(optimizer_constructor, attrs::Pair...)
```

Groups an optimizer constructor with the list of attributes `attrs`. Note that it is equivalent to `MOI.OptimizerWithAttributes`.

When provided to the `Model` constructor or to [`set_optimizer`](@ref), it creates an optimizer by calling `optimizer_constructor()`, and then sets the attributes using [`set_attribute`](@ref).

See also: [`set_attribute`](@ref), [`get_attribute`](@ref).

## Note

The string names of the attributes are specific to each solver. One should consult the solver's documentation to find the attributes of interest.

## Example

```jldoctest
julia> import HiGHS

julia> optimizer = optimizer_with_attributes(
           HiGHS.Optimizer, "presolve" => "off", MOI.Silent() => true,
       );

julia> model = Model(optimizer);
```

is equivalent to:

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_attribute(model, "presolve", "off")

julia> set_attribute(model, MOI.Silent(), true)
```
