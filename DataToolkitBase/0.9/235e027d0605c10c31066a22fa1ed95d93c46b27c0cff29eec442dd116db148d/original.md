```
Identifier(dataset::DataSet, collection::Union{Symbol, Nothing}=:name,
           name::Symbol=something(collection, :name))
```

Create an `Identifier` referring to `dataset`, specifying the collection `dataset` comes from as well (when `collection` is not `nothing`) as all of its parameters, but without any type information.

Should `collection` and `name` default to the symbol `:name`, which signals that the collection and dataset reference of the generated `Identifier` should use the *name*s of the collection/dataset. If set to `:uuid`, the UUID is used instead. No other value symbols are supported.
