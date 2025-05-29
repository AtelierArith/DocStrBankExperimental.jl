```
test_object_class(
    obj_class::ObjectClass,
    rel_class::RelationshipClass,
    m::Module = @__MODULE__;
    count_min::Real = 0,
    count_max::Real = Inf,
    limit::Real = Inf,
)
```

Test if the `object_class` in module `m` is included in `relationship_class` with a desired entry count for each `object`. The `limit` keyword can be used to limit the number of tests performed.
