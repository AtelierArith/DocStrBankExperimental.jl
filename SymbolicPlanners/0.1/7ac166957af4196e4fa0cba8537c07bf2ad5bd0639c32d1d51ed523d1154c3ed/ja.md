```
Specification(problem::Problem)
```

PDDL `Problem` に含まれる情報に基づいて、適切な具体的な型の `Specification` を構築します。メトリックの式が指定されていない場合、[`MinStepsGoal`](@ref) の仕様が返されます。それ以外の場合は、[`MinMetricGoal`](@ref) または [`MaxMetricGoal`](@ref) のいずれかが返されます。
