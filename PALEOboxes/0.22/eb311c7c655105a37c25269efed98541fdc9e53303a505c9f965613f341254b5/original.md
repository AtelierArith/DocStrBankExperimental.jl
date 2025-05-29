```
Parameter{T, ParseFromString}
```

A reaction parameter of type `T`.

Create using short names `ParDouble`, `ParInt`, `ParBool`, `ParString`.

Read value as `<par>[]`, set with [`setvalue!`](@ref).

Parameters with `external=true` may be set from the Model-level Parameters list, if `name` is present in that list.

`ParseFromString` should usually be `Nothing`: a value of `Type T` is then required when calling [`setvalue!`](@ref). If `ParseFromString` is not `Nothing`, then [`setvalue!`](@ref) will accept an `AbstractString` and call `Base.parse(ParseFromString, strvalue)`. This allows eg an enum-valued Parameter to be defined by Parameter{EnumType, EnumType} and implementing parse(EnumType, rawvalue::AbstractString)
