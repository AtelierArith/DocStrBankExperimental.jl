```
refine!(sol::Solution, planner::Planner, domain::Domain, state::State, spec)
```

既存の解 (`sol`) を計画問題に対して洗練させます（インプレース）。`spec` 引数は `Specification` として、または満たすべき1つ以上の目標 `Term` として提供できます。
