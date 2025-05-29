```
build_solver_instances(;
    nlp_solver::Union{Missing,JuMP.MOI.OptimizerWithAttributes}=missing,
    mip_solver::Union{Missing,JuMP.MOI.OptimizerWithAttributes}=missing,
    minlp_solver::Union{Missing,JuMP.MOI.OptimizerWithAttributes}=missing,
    misocp_solver::Union{Missing,JuMP.MOI.OptimizerWithAttributes}=missing,
    solver_options::Dict{String,<:Any}=Dict{String,Any}(),
    log_level::String="warn",
)::Dict{String,Any}
```

Returns solver instances as a Dict ready for use with JuMP Models, for NLP (`"nlp_solver"`), MIP (`"mip_solver"`), MINLP (`"minlp_solver"`), and (MI)SOC (`"misocp_solver"`) problems.

  * `nlp_solver` (default: `missing`): If missing, will use Ipopt as NLP solver, or KNITRO if `knitro=true`
  * `mip_solver` (default: `missing`): If missing, will use Cbc as MIP solver, or Gurobi if `gurobi==true`
  * `minlp_solver` (default: `missing`): If missing, will use Juniper with `nlp_solver` and `mip_solver`, of KNITRO if `knitro=true`
  * `misocp_solver` (default: `missing`): If missing will use Juniper with `mip_solver`, or Gurobi if `gurobi==true`
  * `solver_options` (default: Dict{String,Any}())
  * `log_level` (default: "warn")
