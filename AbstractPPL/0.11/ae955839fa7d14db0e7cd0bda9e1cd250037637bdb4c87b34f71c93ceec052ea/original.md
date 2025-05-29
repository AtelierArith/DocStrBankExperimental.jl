```
dict_to_index(dict)
dict_to_index(symbol_val, dict)
```

Convert a dictionary representation of an index `dict` to an index.

Users can extend the functionality of `dict_to_index` (and hence `VarName` de/serialisation) by extending this method along with [`index_to_dict`](@ref). Specifically, suppose you have a custom index type `MyIndexType` and you want to be able to de/serialise a `VarName` containing this index type. You should then implement the following two methods:

1. `AbstractPPL.index_to_dict(i::MyModule.MyIndexType)` should return a dictionary representation of the index `i`. This dictionary must contain the key `"type"`, and the corresponding value must be a string that uniquely identifies the index type. Generally, it makes sense to use the name of the type (perhaps prefixed with module qualifiers) as this value to avoid clashes. The remainder of the dictionary can have any structure you like.
2. Suppose the value of `index_to_dict(i)["type"]` is `"MyModule.MyIndexType"`. You should then implement the corresponding method `AbstractPPL.dict_to_index(::Val{Symbol("MyModule.MyIndexType")}, dict)`, which should take the dictionary representation as the second argument and return the original `MyIndexType` object.

To see an example of this in action, you can look in the the AbstractPPL test suite, which contains a test for serialising OffsetArrays.
