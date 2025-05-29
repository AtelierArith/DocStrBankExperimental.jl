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

JuMPモデルで使用するための辞書として準備されたソルバーインスタンスを返します。NLP（`"nlp_solver"`）、MIP（`"mip_solver"`）、MINLP（`"minlp_solver"`）、および（MI）SOC（`"misocp_solver"`）問題に対応しています。

  * `nlp_solver`（デフォルト: `missing`）：指定がない場合、NLPソルバーとしてIpoptを使用します。`knitro=true`の場合はKNITROを使用します。
  * `mip_solver`（デフォルト: `missing`）：指定がない場合、MIPソルバーとしてCbcを使用します。`gurobi==true`の場合はGurobiを使用します。
  * `minlp_solver`（デフォルト: `missing`）：指定がない場合、`nlp_solver`と`mip_solver`を使用してJuniperを使用します。`knitro=true`の場合はKNITROを使用します。
  * `misocp_solver`（デフォルト: `missing`）：指定がない場合、`mip_solver`を使用してJuniperを使用します。`gurobi==true`の場合はGurobiを使用します。
  * `solver_options`（デフォルト: Dict{String,Any}())
  * `log_level`（デフォルト: "warn"）
