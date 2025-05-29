Attribute that contains information regarding forced outages where the transition probabilities are modeled with geometric distributions. The outage probabilities and recovery probabilities can be modeled as time series.

# Arguments

  * `time_to_recovery::Int`: Time elapsed to recovery after a failure in Milliseconds.
  * `outage_transition_probability::Float64`: Characterizes the probability of failure (1 - p) in the geometric distribution.
  * `internal::InfrastructureSystemsInternal`: power system internal reference, do not modify
