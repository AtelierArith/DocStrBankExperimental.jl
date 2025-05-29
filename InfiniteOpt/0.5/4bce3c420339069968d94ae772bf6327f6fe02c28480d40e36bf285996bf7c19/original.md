```
InfiniteModel <: JuMP.AbstractModel
```

A `DataType` for storing all of the mathematical modeling information needed to model an optmization problem with an infinite-dimensional decision space.

**Fields**

  * `independent_params::MOIUC.CleverDict{IndependentParameterIndex, ScalarParameterData{IndependentParameter}}`:  The independent parameters and their mapping information.
  * `dependent_params::MOIUC.CleverDict{DependentParametersIndex, MultiParameterData}`:  The dependent parameters and their mapping information.
  * `finite_params::MOIUC.CleverDict{FiniteParameterIndex, ScalarParameterData{FiniteParameter}}`:  The finite parameters and their mapping information.
  * `name_to_param::Union{Dict{String, AbstractInfOptIndex}, Nothing}`:  Field to help find a parameter given the name.
  * `last_param_num::Int`: The last parameter number to be used.
  * `param_object_indices::Vector{Union{IndependentParameterIndex, DependentParametersIndex}}`: The collection of parameter object indices in creation order.
  * `param_functions::MOIUC.CleverDict{ParameterFunctionIndex, ParameterFunctionData{ParameterFunction}}`:  The infinite parameter functions and their mapping information.
  * `infinite_vars::MOIUC.CleverDict{InfiniteVariableIndex, <:VariableData{<:InfiniteVariable}}`:  The infinite variables and their mapping information.
  * `semi_infinite_vars::MOIUC.CleverDict{SemiInfiniteVariableIndex, <:VariableData{<:SemiInfiniteVariable}}`:  The semi-infinite variables and their mapping information.
  * `semi_lookup::Dict{<:Tuple, SemiInfiniteVariableIndex}`: Look-up if a variable already already exists.
  * `point_vars::MOIUC.CleverDict{PointVariableIndex, <:VariableData{<:PointVariable}}`:  The point variables and their mapping information.
  * `point_lookup::Dict{<:Tuple, PointVariableIndex}`: Look-up if a variable already exists.
  * `finite_vars::MOIUC.CleverDict{FiniteVariableIndex, VariableData{JuMP.ScalarVariable{Float64, Float64, Float64, Float64}}}`:  The finite variables and their mapping information.
  * `name_to_var::Union{Dict{String, AbstractInfOptIndex}, Nothing}`:  Field to help find a variable given the name.
  * `derivatives::MOIUC.CleverDict{DerivativeIndex, <:VariableData{<:Derivative}}`: The derivatives and their mapping information.
  * `deriv_lookup::Dict{<:Tuple, DerivativeIndex}`: Map derivative variable-parameter  pairs to a derivative index to prevent duplicates.
  * `measures::MOIUC.CleverDict{MeasureIndex, <:MeasureData}`:  The measures and their mapping information.
  * `integral_defaults::Dict{Symbol}`:  The default keyword arguments for [`integral`](@ref).
  * `constraints::MOIUC.CleverDict{InfOptConstraintIndex, <:ConstraintData}`:  The constraints and their mapping information.
  * `constraint_restrictions::Dict{InfOptConstraintIndex, <:DomainRestrictions}` Map constraints  to their domain restrictions if they have any.
  * `name_to_constr::Union{Dict{String, InfOptConstraintIndex}, Nothing}`:  Field to help find a constraint given the name.
  * `objective_sense::MOI.OptimizationSense`: Objective sense.
  * `objective_function::JuMP.AbstractJuMPScalar`: Finite scalar function.
  * `objective_has_measures::Bool`: Does the objective contain measures?
  * `registrations::Vector{RegisteredFunction}`: The nonlinear registered functions.
  * `Dict{Tuple{Symbol, Int}, Function}`: Map a name and number of arguments to a registered function.
  * `obj_dict::Dict{Symbol, Any}`: Store Julia symbols used with `InfiniteModel`
  * `optimizer_constructor`: MOI optimizer constructor (e.g., Gurobi.Optimizer).
  * `optimizer_model::JuMP.Model`: Model used to solve `InfiniteModel`
  * `ready_to_optimize::Bool`: Is the optimizer_model up to date.
  * `ext::Dict{Symbol, Any}`: Store arbitrary extension information.
