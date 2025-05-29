```
infer_action_costs(
    domain::Domain, state::State, metric::Term,
    cost_fluents=PDDL.constituents(metric, domain),
    static_fluents=infer_static_fluents(domain)
)
```

Infer fixed action costs for a `domain` and initial `state`, and `metric` formula, returning `nothing` if unsuccessful.
