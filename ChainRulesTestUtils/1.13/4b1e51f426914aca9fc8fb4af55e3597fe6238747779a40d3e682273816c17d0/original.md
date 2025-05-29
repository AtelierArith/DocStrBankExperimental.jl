```
test_method_tables()
```

Checks that the method tables for `rrule` and `frule` are sensible. This in future may carry out a number of checks, but presently just checks to make sure that no rules have been added to the very general `DataType`, `Union` or `UnionAll` types, which is easy to do accidentally when writing rules for constructors. It happens if you write e.g. `rrule(::typeof(Foo), x)` rather than `rrule(::Type{<:Foo}, x)`. This would then actually define `rrule(::DataType, x)`. (or `UnionAll` if `Foo` was parametric, or `Union` if `Foo` was a type alias for a `Union`)
