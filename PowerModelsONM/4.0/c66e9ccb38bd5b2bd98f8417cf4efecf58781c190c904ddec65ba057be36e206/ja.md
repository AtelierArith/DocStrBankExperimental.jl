```
constraint_mc_load_power(pm::PMD.LPUBFDiagModel, load_id::Int, scen::Int; nw::Int=nw_id_default, report::Bool=true)
```

LPUBFDiagModelのための負荷モデル（PMD.constraint*mc*load_powerに似ています）をロバストmld問題のためにロードします。制約は各シナリオごとに異なります。
