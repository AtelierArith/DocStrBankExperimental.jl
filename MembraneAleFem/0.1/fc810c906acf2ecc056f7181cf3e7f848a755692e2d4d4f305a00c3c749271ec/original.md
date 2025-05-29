```
get_scenario_bc_info(numnp, IX, bdry_nodes, ..., p::Params; args...)
```

Return [`Scenario`](@ref)-specific information for the provided `Params`.

Each of the functions called returns `(dofs, ndf, ID, inh_dir_bcs, inh_neu_bcs)`, in that order.
