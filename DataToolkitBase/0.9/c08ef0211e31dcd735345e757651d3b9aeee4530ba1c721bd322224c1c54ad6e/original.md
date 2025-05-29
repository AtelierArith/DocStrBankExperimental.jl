```
@advise [source] f(args...; kwargs...)
```

Convert a function call `f(args...; kwargs...)` to an *advised* function call, where the advise collection is obtained from `source` or the first data-like* value of `args`.

* i.e. a `DataCollection`, `DataSet`, or `AbstractDataTransformer`

For example, `@advise myfunc(other, somedataset, rest...)` is equivalent to `somedataset.collection.advise(myfunc, other, somedataset, rest...)`.

This macro performs a fairly minor code transformation, but should improve clarity.
