Represents a sanitation technology. `Source` and `Sink` are aliases.

Has the following fields:

  * `inputs::Vector{Santiago.Product}`
  * `outputs::Vector{Santiago.Product}`
  * `name::String`
  * `functional_group::Symbol`
  * `appscore::Array{Float64}`: Appropriateness score for a given case.
  * `n_inputs::Int64`
  * `transC::Dict{String, Dict{Santiago.Product, Float64}}`: Transfer coefficients
  * `transC_reliability::Dict{String, Float64}`: Uncertainty factor relating to transfer coefficients
