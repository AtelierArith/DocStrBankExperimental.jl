```
InfiniteModel <: JuMP.AbstractModel
```

最適化問題を無限次元の意思決定空間でモデル化するために必要なすべての数学的モデリング情報を格納するための`DataType`。

**フィールド**

  * `independent_params::MOIUC.CleverDict{IndependentParameterIndex, ScalarParameterData{IndependentParameter}}`:  独立パラメータとそのマッピング情報。
  * `dependent_params::MOIUC.CleverDict{DependentParametersIndex, MultiParameterData}`:  従属パラメータとそのマッピング情報。
  * `finite_params::MOIUC.CleverDict{FiniteParameterIndex, ScalarParameterData{FiniteParameter}}`:  有限パラメータとそのマッピング情報。
  * `name_to_param::Union{Dict{String, AbstractInfOptIndex}, Nothing}`:  名前からパラメータを見つけるのに役立つフィールド。
  * `last_param_num::Int`: 使用される最後のパラメータ番号。
  * `param_object_indices::Vector{Union{IndependentParameterIndex, DependentParametersIndex}}`: 作成順序でのパラメータオブジェクトインデックスのコレクション。
  * `param_functions::MOIUC.CleverDict{ParameterFunctionIndex, ParameterFunctionData{ParameterFunction}}`:  無限パラメータ関数とそのマッピング情報。
  * `infinite_vars::MOIUC.CleverDict{InfiniteVariableIndex, <:VariableData{<:InfiniteVariable}}`:  無限変数とそのマッピング情報。
  * `semi_infinite_vars::MOIUC.CleverDict{SemiInfiniteVariableIndex, <:VariableData{<:SemiInfiniteVariable}}`:  半無限変数とそのマッピング情報。
  * `semi_lookup::Dict{<:Tuple, SemiInfiniteVariableIndex}`:  変数がすでに存在するかどうかを調べる。
  * `point_vars::MOIUC.CleverDict{PointVariableIndex, <:VariableData{<:PointVariable}}`:  点変数とそのマッピング情報。
  * `point_lookup::Dict{<:Tuple, PointVariableIndex}`:  変数がすでに存在するかどうかを調べる。
  * `finite_vars::MOIUC.CleverDict{FiniteVariableIndex, VariableData{JuMP.ScalarVariable{Float64, Float64, Float64, Float64}}}`:  有限変数とそのマッピング情報。
  * `name_to_var::Union{Dict{String, AbstractInfOptIndex}, Nothing}`:  名前から変数を見つけるのに役立つフィールド。
  * `derivatives::MOIUC.CleverDict{DerivativeIndex, <:VariableData{<:Derivative}}`:  導関数とそのマッピング情報。
  * `deriv_lookup::Dict{<:Tuple, DerivativeIndex}`:  導関数変数-パラメータペアを導関数インデックスにマップして重複を防ぐ。
  * `measures::MOIUC.CleverDict{MeasureIndex, <:MeasureData}`:  測定とそのマッピング情報。
  * `integral_defaults::Dict{Symbol}`:  [`integral`](@ref)のデフォルトキーワード引数。
  * `constraints::MOIUC.CleverDict{InfOptConstraintIndex, <:ConstraintData}`:  制約とそのマッピング情報。
  * `constraint_restrictions::Dict{InfOptConstraintIndex, <:DomainRestrictions}`:  制約をそのドメイン制限にマップする（あれば）。
  * `name_to_constr::Union{Dict{String, InfOptConstraintIndex}, Nothing}`:  名前から制約を見つけるのに役立つフィールド。
  * `objective_sense::MOI.OptimizationSense`:  目的の感覚。
  * `objective_function::JuMP.AbstractJuMPScalar`:  有限スカラー関数。
  * `objective_has_measures::Bool`:  目的に測定が含まれていますか？
  * `registrations::Vector{RegisteredFunction}`:  非線形登録関数。
  * `Dict{Tuple{Symbol, Int}, Function}`:  名前と引数の数を登録関数にマップする。
  * `obj_dict::Dict{Symbol, Any}`:  `InfiniteModel`で使用されるJuliaシンボルを格納。
  * `optimizer_constructor`:  MOIオプティマイザコンストラクタ（例：Gurobi.Optimizer）。
  * `optimizer_model::JuMP.Model`:  `InfiniteModel`を解決するために使用されるモデル。
  * `ready_to_optimize::Bool`:  optimizer_modelは最新ですか。
  * `ext::Dict{Symbol, Any}`:  任意の拡張情報を格納。
