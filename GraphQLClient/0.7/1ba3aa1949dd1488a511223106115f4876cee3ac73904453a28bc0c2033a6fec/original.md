```
introspect_object([client::Client],
                  object_name;
                  force=false,
                  reset_all=false,
                  parent_type=nothing,
                  parent_map=Dict{String, Type}(),
                  mutable=true,
                  allowed_level=2,
                  custom_scalar_types=Dict{String, DataType}())
```

Introspects an object and creates a Julia type.

Due to the recursion that is possible with GraphQL schemas, this introspection can be difficult. Please read this docstring carefully.

# Parent Type

All introspected type, by default, will be given the parent type `AbstractIntrospectedStruct`. The parent type of the top level object being introspected can be set by `parent_type`, and the parent types of any object being introspected can be set using the `parent_map` dictionary. If `object_type` is a key in `parent_map` and `parent_type` is not `nothing`, the value of `parent_type` will take precedence.

# StructTypes

`AbstractIntrospectedStruct` has a defined `StructType` of `Struct` for JSON serialisation. You can define `StructType`s for the concrete type that is introspected by doing

```
StructTypes.StructType(::Type{GraphQLClient.get_introspected_object(object_name)}) = StructTypes.Struct()
```

# Recursion

Recursion is handled by two methods:

1. Providing the `allowed_level` kwarg to control how deep introspection goes.
2. Maintaining a list of objects that are currently being introspected. No object can be instrospected  twice and a type cannot be used in a type definition until it has been defined itself. Therefore  if this situation occurs, the fields that need to use the not-yet-defined type are ignored.  This means the order in which objects are intropsected can have an impact on the final structs.

For example consider the following objects

```
Country:
 - name: String
 - leader: Person

Person:
 - name: String
 - countryOfBirth: Country
```

If we introspected `Country` first, the `Person` object would not contain the `countryOfBirth` field, as it is impossible to set the type of that field to `Country` before it is defined itself. If we introspected `Person` first, the `Country` boject would not contain the `leader` field for the same reason.

# Keyword Arguments

  * `force=false`: if `false`, the introspection will use already introspected types for objects   if they exist. If `true`, any previously introspected types will be overwritten if they   are introspected whilst introspecting `object_name`. Use with caution, as other types   may rely on types that are then overwritten.
  * `reset_all`: delete all introspected types to start from a clean sheet.
  * `parent_type=nothing`: the parent type to give to the new introspected struct. See   comment above.
  * `parent_map=Dict{String, Type}()`: dictionary to maps   object names to desired parent types. If `parent_type` is supplied, this value   will take precedence over the entry in `parent_map` for `object_name`.
  * `mutable=true`: boolean to set the mutability of top level and all lower level types.
  * `allowed_level=2`: how many levels of introspection are allowed. For example, if this   is `1` then only top level fields that are objects will be in the introspected type.
  * `custom_scalar_types`: dictionary of custom GraphQL scalar type to Julia type. This kwarg enables   custom scalar types to be introspected to the correct type.
