```julia
import_ocp_solution(
    ::CTModels.JSON3Tag,
    args...;
    kwargs...
) -> CTModels.Solution{TimeGridModelType, TimesModelType, StateModelType, ControlModelType, VariableModelType, CostateModelType, Float64, DualModelType, CTModels.SolverInfos{Dict{Symbol, Any}}} where {TimeGridModelType<:CTModels.TimeGridModel, TimesModelType<:CTModels.TimesModel, StateModelType<:Union{CTModels.StateModelSolution{TS} where TS<:CTModels.var"#111#133", CTModels.StateModelSolution{TS} where TS<:CTModels.var"#112#134"}, ControlModelType<:Union{CTModels.ControlModelSolution{TS} where TS<:CTModels.var"#113#135", CTModels.ControlModelSolution{TS} where TS<:CTModels.var"#114#136"}, VariableModelType<:Union{CTModels.VariableModelSolution{Vector{Float64}}, CTModels.VariableModelSolution{Float64}}, CostateModelType<:Union{CTModels.var"#115#137", CTModels.var"#116#138"}, DualModelType<:(CTModels.DualModel{PC_Dual, BC_Dual, SC_LB_Dual, SC_UB_Dual, CC_LB_Dual, CC_UB_Dual, VC_LB_Dual, VC_UB_Dual} where {PC_Dual<:Union{Nothing, CTModels.var"#118#140", CTModels.var"#119#141"}, BC_Dual<:Union{Nothing, Vector{Float64}}, SC_LB_Dual<:Union{Nothing, CTModels.var"#121#143", CTModels.var"#122#144"}, SC_UB_Dual<:Union{Nothing, CTModels.var"#124#146", CTModels.var"#125#147"}, CC_LB_Dual<:Union{Nothing, CTModels.var"#127#149", CTModels.var"#128#150"}, CC_UB_Dual<:Union{Nothing, CTModels.var"#130#152", CTModels.var"#131#153"}, VC_LB_Dual<:Union{Nothing, Vector{Float64}}, VC_UB_Dual<:Union{Nothing, Vector{Float64}}})}

```

JLDファイルからソリューションをインポートします。
