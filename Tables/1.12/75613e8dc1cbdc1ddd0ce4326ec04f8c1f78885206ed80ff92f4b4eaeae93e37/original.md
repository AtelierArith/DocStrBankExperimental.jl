```
Tables.istable(x) => Bool
```

Check if an object has specifically defined that it is a table. Note that not all valid tables will return true, since it's possible to satisfy the Tables.jl interface at "run-time", e.g. a `Generator` of `NamedTuple`s iterates `NamedTuple`s, which satisfies the `AbstractRow` interface, but there's no static way of knowing that the generator is a table.

It is recommended that for users implementing `MyType`, they define only `istable(::Type{MyType})`. `istable(::MyType)` will then automatically delegate to this method.

`istable` calls `TableTraits.isiterabletable` as a fallback. This can have a considerable runtime overhead in some contexts. To avoid these and use `istable` as a compile-time trait, it can be called on a type as `istable(typeof(obj))`.
