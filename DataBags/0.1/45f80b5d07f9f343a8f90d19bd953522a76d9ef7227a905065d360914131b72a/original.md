```
wrap(T::Type{<:AbstractDataBag}, arg) -> obj::T
```

wraps argument `arg` in a data-bag of type `T`.  The returned object shares its contents with `arg`.

This method can be used to build a data-bag from an existing dictionary without duplicating the dictionary.  As an example:

```
dict = Dict{Symbol,Any}(:a => 1, :foo => "bar")
cont = wrap(DataBag, dict)
cont.b = 33
dict["b"] == 33 # yields `true`
```

If the statement `wrap(DataBag, dict)` is replaced by `DataBag(dict)`, the result of the last statement is `false`.
