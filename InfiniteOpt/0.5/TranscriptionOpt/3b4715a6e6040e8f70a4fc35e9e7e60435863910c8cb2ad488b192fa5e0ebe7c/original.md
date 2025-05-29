```
TranscriptionData
```

A DataType for storing the data mapping an [`InfiniteOpt.InfiniteModel`](@ref) that has been transcribed to a regular `JuMP.Model` that contains the transcribed variables. This is stored in the `ext` field of a `JuMP.Model` to make what is called a `TranscriptionModel` via the [`TranscriptionModel`](@ref) constructor.

**Fields**

  * `infvar_lookup::Dict{InfiniteOpt.GeneralVariableRef, Dict{Vector{Float64}, Int}}`:  A lookup table of infinite variable transcriptions via support value.
  * `infvar_mappings::Dict{InfiniteOpt.GeneralVariableRef, Vector{JuMP.VariableRef}}`:  Map infinite variables to their transcription variables.
  * `infvar_supports::Dict{InfiniteOpt.GeneralVariableRef, Vector{Tuple}}`:  Map infinite variables to their support values.
  * `infvar_support_labels::Dict{InfiniteOpt.GeneralVariableRef, Vector{Set{DataType}}}`:   Map the infinite variables to their support labels.
  * `finvar_mappings::Dict{InfiniteOpt.GeneralVariableRef, JuMP.VariableRef}`:  Map finite variables to their transcription variables.
  * `semi_infinite_vars::Vector{InfiniteOpt.SemiInfiniteVariable{InfiniteOpt.GeneralVariableRef}}`:  Store the core semi-infinite variable objects of semi-infinite variables formed on transcription.
  * `semi_lookup::Dict{Tuple{InfiniteOpt.GeneralVariableRef, Dict{Int, Float64}}, InfiniteOpt.GeneralVariableRef}`:  Lookup which semi-infinite variables have already been added.
  * `last_point_index::Int`: The last internal point variable index added.
  * `point_lookup::Dict{Tuple{InfiniteOpt.GeneralVariableRef, Vector{Float64}}, InfiniteOpt.GeneralVariableRef}`:  Lookup which point variables have already been created internally.
  * `measure_lookup::Dict{InfiniteOpt.GeneralVariableRef, Dict{Vector{Float64}, Int}}`:  A lookup table of measure transcriptions via support value.
  * `measure_mappings::Dict{InfiniteOpt.GeneralVariableRef, Vector{JuMP.AbstractJuMPScalar}}`:  Map measures to transcription expressions.
  * `measure_supports::Dict{InfiniteOpt.GeneralVariableRef, Vector{Tuple}}`:  Map measures to their supports values (if the transcribed measure is still infinite).
  * `measure_support_labels::Dict{InfiniteOpt.GeneralVariableRef, Vector{Set{DataType}}}`:   Map measures to their support labels if they have any.
  * `constr_mappings::Dict{InfiniteOpt.InfOptConstraintRef, Vector{JuMP.ConstraintRef}}`:  Map constraints to their transcriptions.
  * `constr_supports::Dict{InfiniteOpt.InfOptConstraintRef, Vector{Tuple}}`:  Map constraints to their support values.
  * `constr_support_labels::Dict{InfiniteOpt.InfOptConstraintRef, Vector{Set{DataType}}}`:   Map constraints to their support labels.
  * `supports::Tuple`: Store the collected parameter supports here.
  * `support_labels::Tuple`: Store the collected parameter labels here.
  * `has_internal_supports::Bool`: Where any internal supports collected?
