```
test_parameter(
    param::Parameter,
    value_type::Union{DataType,Union,UnionAll},
    m::Module = @__MODULE__;
    value_min::Real = -Inf,
    value_max::Real = Inf,
    limit::Real = Inf,
)
```

Test if `param` value in module `m` has the expected `DataType` and is contained between `value_min`, and `value_max`. The `limit` keyword can be used to limit the number of tests performed.

Methods are provided for testing `ObjectClass` and `RelationshipClass` separately.
