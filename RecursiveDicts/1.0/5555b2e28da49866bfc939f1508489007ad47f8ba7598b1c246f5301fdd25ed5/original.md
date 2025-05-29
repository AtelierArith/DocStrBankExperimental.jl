```
RecursiveDict{K,V} <: AbstractDict{K,Union{V,RecursiveDict}}
```

A `Dict` where an instance of itself is always a valid value.  So a `RecursiveDict{String,String}` has `String` keys, and the values may be either `String`s or a `RecursiveDict{String,String}`. It's harmless to write this as `RecursiveDict{String,Union{String,RecursiveDict{String,String}}}`, although it isn't necessary, and as the signature gestures at, one does have to provide the base case eventually.

Implements all `Base` methods which take a `Dict`.  `convert` will return the wrapped `Dict` which provides the data structure, as a shared reference, meaning changes to the provided `Dict` will be seen in the `RecursiveDict`, so this data structure may be used anywhere which expects a `Dict`, with a bit of care.

A `Dict{K,V}` may also be converted to a `RecursiveDict{K,V}`, without copying.
