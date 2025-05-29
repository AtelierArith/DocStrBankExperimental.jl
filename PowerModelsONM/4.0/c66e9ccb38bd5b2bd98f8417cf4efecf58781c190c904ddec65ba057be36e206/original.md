```
constraint_mc_load_power(pm::PMD.LPUBFDiagModel, load_id::Int, scen::Int; nw::Int=nw_id_default, report::Bool=true)
```

Load models for LPUBFDiagModel (similar to PMD.constraint*mc*load_power) for robust mld problem. The constraints are different for each scenario.
