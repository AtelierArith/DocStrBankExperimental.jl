Converts raw data to the appropriate data type.

# Parameters

  * `datatype::Type`: the datatype.
  * `depvar_data::Union{Vector{Float32}, Vector{Float64}, Vector{Union{Float32, Missing}}, Vector{Union{Float64, Missing}}}`: dependent variable data.
  * `expvars_data::Union{Array{Float32}, Array{Float64}, Array{Union{Float32, Missing}}, Array{Union{Float64, Missing}}}`: explanatory variables data.
  * `fixedvariables::Union{Array{Float32}, Array{Float64}, Array{Union{Float32, Missing}}, Array{Union{Float64, Missing}}, Nothing}`: fixed variables data.
  * `time_data::Union{Array{Float32}, Array{Float64}, Array{Union{Float32, Missing}}, Array{Union{Float64, Missing}}, Nothing}`: time variable data.
  * `panel_data::Union{Array{Float32}, Array{Float64}, Array{Union{Float32, Missing}}, Array{Union{Float64, Missing}}, Nothing}`: panel variable data.
