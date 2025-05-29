```
create(T::Type{<:AbstractDataTransformer}, driver::Symbol, source::String, dataset::DataSet;
       minpriority::Int=-100, maxpriority::Int=100)
```

Create a new `T` with driver `driver` from `source`/`dataset`.

If `driver` is the symbol `*` then all possible drivers are checked and the highest priority (according to `createpriority`) valid driver used. Drivers with a priority outside `minpriority`–`maxpriority` will not be considered.

The created data transformer is returned, unless the given `driver` is not valid, in which case `nothing` is returned instead.
