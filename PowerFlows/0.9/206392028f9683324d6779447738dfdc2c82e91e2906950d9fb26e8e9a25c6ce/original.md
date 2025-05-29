Returns a dictionary containing the AC power flow results.

Only single-period evaluation is supported at the moment for AC Power flows. Resulting dictionary will therefore feature just one key linked to one DataFrame.

# Arguments:

  * `::ACPowerFlow`:       use ACPowerFlow() storing AC power flow results.
  * `sys::PSY.System`:       container storing the systam information.
  * `result::Vector{Float64}`:       vector containing the reults for one single time-period.
