```
get_scenario_bc_info(numnp, IX, bdry_nodes, ..., p::Params; args...)
```

提供された `Params` に対して [`Scenario`](@ref) 特有の情報を返します。

呼び出される各関数は、(dofs, ndf, ID, inh*dir*bcs, inh*neu*bcs) の順で返します。
