```
MaximalSetIterator{T<:AbstractFiniteSetCollection}
```

An object used for iterating over the maximal (by set inclusion) elements of a collection. The typical user of this package will not need to explicitly construct an object of this type; rather, the [`facets`](@ref) function (equivalently, the [`max`](@ref) function) can be used anywhere an iterable collection could be used.
