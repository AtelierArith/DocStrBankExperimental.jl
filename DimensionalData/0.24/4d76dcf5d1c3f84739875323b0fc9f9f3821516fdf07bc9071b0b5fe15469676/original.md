```
rebuild(x, args...)
rebuild(x; kw...)
```

Rebuild an object struct with updated field values.

`x` can be a `AbstractDimArray`, a `Dimension`, `LookupArray` or other custom types.

This is an abstraction that alows inbuilt and custom types to be rebuilt to update their fields, as most objects in DimensionalData.jl are immutable.

The arguments version can be concise but depends on a fixed order defined for some DimensionalData objects. It should be defined based on the object type in DimensionalData, adding the fields specific to your object.

The keyword version ignores order, and is mostly automated  using `ConstructionBase.setproperties`. It should only be defined if your object has  missing fields or fields with different names to DimensionalData objects.

The arguments required are defined for the abstract type that has a `rebuild` method.
