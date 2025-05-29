Abstract supertype for model wrappers like `Model`, useful if you need to extend the behaviour of this package.

# Accessing `AbstactModel` parameters

Fields can be accessed with `getindex`:

```julia
model = Model(obj)
@assert model[:val] isa Tuple
@assert model[:val] == model[:val]
@assert model[:units] == model[:units]
```

To get a combined Tuple of `val` and `units`, use [`withunits`](@ref).

The type name of the parent model component, and the field name are also available:

```julia
model[:component]
model[:fieldname]
```

## Getting a `Vector` of parameter values

`Base` methods `collect`, `vec`, and `Array` return a vector of the result of  `model[:val]`. To get a vector of other parameter fields, simply `collect` the tuple:

```julian
boundsvec = collect(model[:bounds])
```

## Tables.jl interface

All `AbstractModel`s define the Tables.jl interface. This means their paremeters and parameter metadata can be converted to a `DataFrame` or CSV very easily:

```julia
df = DataFrame(model)
```

Tables.rows will also return all `Param`s as a `Vector` of `NamedTuple`.

To update a model with params from a table, use `update!` or `update`:

```julia
update!(model, table)
```

## `AbstractModel` Interface: Defining your own model wrappers

It may be simplest to use `ModelParameters.jl` on a wrapper type you also use for other  things. This is what DynamicGrids.jl does with `Ruleset`. It's straightforward to extend  the interface, nearly everything is taken care of by inheriting from `AbstractModel`. But  in some circumstances you will need to define additional methods.

`AbstractModel` uses `Base.parent` to return the parent model object. Either use a field `:parent` on your `<: AbstractModel` type, or add a  method to `Base.parent`. 

With a custom `parent` field you will also need to define a method for  [`setparent!`](@ref) and [`setparent`](@ref) that sets the correct field.

An `AbstractModel` with complicated type parameters may require a method of  `ConstructionBase.constructorof`.

To add custom `show` methods but still print the parameter table, you can use:

```julia
printparams(io::IO, model)
```

That should be all you need to do.
