```
JUA_Variant
```

A mutable struct that defines a `JUA_Variant` object - the equivalent of a `UA_Variant`, but with memory managed by Julia rather than C (exceptions below). `JUA_Variant`s can hold any datatype either as a scalar or in array form.

The following constructor methods are defined:

```
JUA_Variant()
```

creates an empty `JUA_Variant`, equivalent to calling `UA_Variant_new()`.

```
JUA_Variant(value::Union{T, AbstractArray{T}}) where T <: Union{UA_NUMBER_TYPES, AbstractString, ComplexF32, ComplexF64, Rational{<:Integer}})
```

creates a `JUA_Variant` containing `value`. All properties of the variant are set automatically. For example, if `value` is an array, then the arrayDimensions and arrayDimensionsSize properties are set based on the number of dimensions and number of elements across each dimension contained in `value`.

```
JUA_Variant(variantptr::Ptr{UA_Variant})
```

creates a `JUA_Variant` based on the pointer `variantptr`. This is a fallback method that can be used to pass `UA_Variant`s generated via the low level interface to the higher level functions. Note that memory management remains on the C side when using this method, i.e., `variantptr` needs to be manually cleaned up with `UA_Variant_delete(variantptr)` after the object is not needed anymore. It is up to the user to ensure this.

Examples:

```
j = JUA_Variant()
j = JUA_Variant("I am a string value")
j = JUA_Variant(["String1", "String2"])
j = JUA_Variant(rand(Float32, 2, 3, 4))
j = JUA_Variant(rand(Int32, 2, 2))
j = JUA_Variant(rand(ComplexF64, 8))
```
