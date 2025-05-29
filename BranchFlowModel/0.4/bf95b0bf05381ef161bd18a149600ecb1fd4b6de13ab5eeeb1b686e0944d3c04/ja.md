```
check_statuses(mg::MetaGraphsNext.MetaGraph)
```

サブモデルのいずれかに `JuMP.termination_status` が `[MOI.OPTIMAL, MOI.ALMOST_OPTIMAL, MOI.LOCALLY_SOLVED]` に含まれていない場合は警告を表示します。
