Establishes the model for a particular services specified by type. Uses the keyword argument `use_service_name` to assign the model to a service with the same name as the name in the template. Uses the keyword argument feedforward to enable passing values between operation model at simulation time

# Arguments

-`::Type{D}`: Power System Service Type -`::Type{B}`: Abstract Service Formulation

# Accepted Key Words

  * `feedforward::Array{<:AbstractAffectFeedforward}` : use to pass parameters between models
  * `use_service_name::Bool` : use the name as the name for the service

# Example

reserves = ServiceModel(PSY.VariableReserve{PSY.ReserveUp}, RangeReserve)
