```
refine!(sol::Solution, planner::Planner, domain::Domain, state::State, spec)
```

Refine an existing solution (`sol`) to a planning problem (in-place). The `spec` argument can be provided as a `Specification` or as one or more goal `Term`s to be satisfied.
