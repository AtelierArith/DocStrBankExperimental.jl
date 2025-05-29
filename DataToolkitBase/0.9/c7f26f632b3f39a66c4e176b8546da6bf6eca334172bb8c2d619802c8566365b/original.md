```
create(T::Type{<:AbstractDataTransformer}, source::String, dataset::DataSet)
```

If `source`/`dataset` can be used to construct a data transformer of type `T`, do so and return it. Otherwise return `nothing`.

Specific transformers should implement specialised forms of this function, that either return `nothing` to indicate that it is not applicable, or a "create spec form". A "create spec form" is simply a list of `key::String => value` entries, giving properties of the to-be-created transformer, e.g.

```
["foo" => "bar",
 "baz" => 2]
```

In addition to accepting TOML-representable values, a `NamedTuple` value can be given that specifies an interactive prompt to put to the user.

```
(; prompt::String = "$key",
   type::Type{String or Bool or <:Number} = String,
   default::type = false or "",
   optional::Bool = false,
   skipvalue::Any = nothing,
   post::Function = identity)
```

The value can also be a `Function` that takes the current specification as an argument and returns a TOML-representable value or `NamedTuple`.

Lastly `true`/`false` can be returned as a convenient way of simply indicating whether an empty (no parameters) driver should be created.
