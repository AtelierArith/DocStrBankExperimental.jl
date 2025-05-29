```
object_dictionary(model::GenericModel)
```

Return the dictionary that maps the symbol name of a variable, constraint, or expression to the corresponding object.

Objects are registered to a specific symbol in the macros. For example, `@variable(model, x[1:2, 1:2])` registers the array of variables `x` to the symbol `:x`.

This method should be defined for any subtype of `AbstractModel`.

See also: [`unregister`](@ref).

## Example

```jldoctest
julia> model = Model();

julia> @variable(model, x[1:2]);

julia> object_dictionary(model)
Dict{Symbol, Any} with 1 entry:
  :x => VariableRef[x[1], x[2]]
```
