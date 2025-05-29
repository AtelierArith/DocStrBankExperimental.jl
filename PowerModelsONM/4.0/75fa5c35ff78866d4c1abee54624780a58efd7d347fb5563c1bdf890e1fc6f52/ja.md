```
run_fault_studies!(
    args::Dict{String,<:Any};
    validate::Bool=true,
    solver::String="nlp_solver"
)::Dict{String,Any}
```

`args["faults"]`が定義されている場合、故障研究を実行し、結果を`args["fault_stuides_results"]`にインプレースで保存します。これは、[`entrypoint`](@ref entrypoint)で使用するためであり、[`run_fault_studies`](@ref run_fault_studies)を使用します。
