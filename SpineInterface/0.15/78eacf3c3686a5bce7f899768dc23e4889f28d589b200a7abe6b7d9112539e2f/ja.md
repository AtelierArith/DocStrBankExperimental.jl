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

モジュール `m` の `object_class` が `relationship_class` に含まれているかを、各 `object` の希望するエントリ数でテストします。`limit` キーワードを使用して、実行されるテストの数を制限することができます。
