```
DataBags.contents(A)
```

yields the contents associated with an instance `A` of a sub-type of `DataBags.AbstractDataBag` or of `AbstractDict`.

This method should be specialized by types derived from `DataBags.AbstractDataBag`, this is the most simple way to inherit of the common behavior implemented by this abstract type.

The `contents` method is also meant to be called by data-bag constructors to create a new dictionary out of their arguments.  For that usage, the syntax is:

```
content(Dict{K,V}, args...; kwds...) -> Dict
```

which yields a new dictionary built out of arguments `args` and keywords `kwds` and accounting for type constraints set by `K` and `V` for respectively the keys and values of the returned dictionary.  Types `K` and/or `V` can be ``Any` if no type constraints are imposed.
