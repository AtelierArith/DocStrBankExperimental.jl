```
function calc_transmission_branch_flow_ac!(
    result::Dict{String,<:Any},
    pmitd_data::Dict{String,<:Any};
)
```

Assumes a valid ac solution is included in the result and computes the branch flow values. Returns the pf solution inside the `pmitd_data` dictionary (not the `result` dictionary). Replicates the _PM function but compatible with PMITD dicitionary.
