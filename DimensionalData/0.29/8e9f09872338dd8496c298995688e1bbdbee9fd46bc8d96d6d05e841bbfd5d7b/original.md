```
rebuild(x; kw...)
```

Rebuild an object struct with updated field values.

`x` can be a `AbstractDimArray`, a `Dimension`, `Lookup` or other custom types.

This is an abstraction that allows inbuilt and custom types to be rebuilt to update their fields, as most objects in DimensionalData.jl are immutable.

Rebuild is mostly automated using `ConstructionBase.setproperties`.  It should only be defined if your object has fields with  with different names to DimensionalData objects. Try not to do that!

The arguments required are defined for the abstract type that has a `rebuild` method.

#### `AbstractBasicDimArray`:

  * `dims`: a `Tuple` of `Dimension`

#### `AbstractDimArray`:

  * `data`: the parent object - an `AbstractArray`
  * `dims`: a `Tuple` of `Dimension`
  * `refdims`: a `Tuple` of `Dimension`
  * `name`: A Symbol, or `NoName` and `Name` on GPU.
  * `metadata`: A `Dict`-like object

#### `AbstractDimStack`:

  * `data`: the parent object, often a `NamedTuple`
  * `dims`, `refdims`, `metadata`

#### `Dimension`:

  * `val`: anything.

#### `Lookup`:

  * `data`: the parent object, an `AbstractArray`
  * Note: argument `rebuild` is deprecated on `AbstractDimArray` and

`AbstractDimStack` in favour of always using the keyword version.  In future the argument version will only be used on `Dimension`, which only have one argument.
