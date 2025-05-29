```
StructBond(T;description = typedescription(T))
```

Create an HTML widget to be used with `@bind` from Pluto that allows to define the custom type `T` by assigning a widget to each of its fields.  The widget will automatically use the docstring of each field as its description if present, or the fieldname otherwise.

When used with `@bind`, it automatically generates a instance of `T` by using the various fields as keyword arguments. *This means that the the structure `T` has to support a keyword-only contruction, such as those generated with `Base.@kwdef` or `Parameters.@with_kw`.

In order to work, the widget (and optionally the description) to associate to eachfield of type `T` has to be provided using the convenience macro `@fielddata`. 

The optional `description` kwarg default to the Type name but can be overridden with anything showable as `MIME"text/html"` 

See also: [`BondTable`](@ref), [`@NTBond`](@ref), [`@BondsList`](@ref), [`Popout`](@ref), [`popoutwrap`](@ref), [`@fielddata`](@ref), [`@fieldhtml`](@ref), [`@typeasfield`](@ref), [`@popoutasfield`](@ref)
