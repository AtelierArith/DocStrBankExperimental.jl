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

モジュール `m` の `relationship_class` が `in_rel_class` に希望する数のエントリで含まれているかをテストします。`limit` キーワードは、実行されるテストの数を制限するために使用できます。
