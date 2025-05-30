```
Tangent{P, T} <: StructuralTangent{P} <: AbstractTangent
```

This type represents the tangent for a `struct`/`NamedTuple`, or `Tuple`. `P` is the the corresponding primal type that this is a tangent for.

`Tangent{P}` should have fields (technically properties), that match to a subset of the fields of the primal type; and each should be a tangent type matching to the primal type of that field. Fields of the P that are not present in the Tangent are treated as `Zero`.

`T` is an implementation detail representing the backing data structure. For Tuple it will be a Tuple, and for everything else it will be a `NamedTuple`. It should not be passed in by user.

For `Tangent`s of `Tuple`s, `iterate` and `getindex` are overloaded to behave similarly to for a tuple. For `Tangent`s of `struct`s, `getproperty` is overloaded to allow for accessing values via `tangent.fieldname`. Any fields not explictly present in the `Tangent` are treated as being set to `ZeroTangent()`. To make a `Tangent` have all the fields of the primal the [`canonicalize`](@ref) function is provided.
