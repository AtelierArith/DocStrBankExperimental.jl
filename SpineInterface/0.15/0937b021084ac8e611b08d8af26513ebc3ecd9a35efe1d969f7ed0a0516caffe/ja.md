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

モジュール `m` 内の `param` 値が期待される `DataType` を持ち、`value_min` と `value_max` の間に含まれているかをテストします。`limit` キーワードは、実行されるテストの数を制限するために使用できます。

`ObjectClass` と `RelationshipClass` を別々にテストするためのメソッドが提供されています。
