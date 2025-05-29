```
Tables.columnnames(::Union{AbstractColumns, AbstractRow}) => Indexable collection
```

Retrieves the list of column names as a 1-based indexable collection (like a `Tuple` or `Vector`) for a `AbstractColumns` or `AbstractRow` interface object. The default definition calls `propertynames(x)`. The returned column names must be unique.
