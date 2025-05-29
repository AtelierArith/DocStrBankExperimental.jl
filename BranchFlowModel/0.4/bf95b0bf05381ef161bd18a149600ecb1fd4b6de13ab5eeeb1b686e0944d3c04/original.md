```
check_statuses(mg::MetaGraphsNext.MetaGraph)
```

Warn if any sub-model has a `JuMP.termination_status` not in `[MOI.OPTIMAL, MOI.ALMOST_OPTIMAL, MOI.LOCALLY_SOLVED]`
