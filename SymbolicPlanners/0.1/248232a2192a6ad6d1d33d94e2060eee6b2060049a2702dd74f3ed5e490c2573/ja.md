```
infer_action_costs(
    domain::Domain, state::State, metric::Term,
    cost_fluents=PDDL.constituents(metric, domain),
    static_fluents=infer_static_fluents(domain)
)
```

`domain` と初期 `state`、および `metric` 形式に対する固定アクションコストを推測し、失敗した場合は `nothing` を返します。
