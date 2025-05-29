```
test_relationship_class(
    rel_class::RelationshipClass,
    in_rel_class::RelationshipClass,
    m::Module = @__MODULE__;
    count_min::Real = 0,
    count_max::Real = Inf,
    limit::Real = Inf,
)
```

Test if `relationship_class` in module `m` is included in `in_rel_class` with the desired number of entries. The `limit` keyword can be used to limit the number of tests performed.
