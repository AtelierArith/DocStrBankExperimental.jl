Function for the definition of the PowerFlowData strucure given the System data, number of time periods to consider and their names. Calling this function will not evaluate the power flows and angles. NOTE: use it for DC power flow computations.

# Arguments:

  * `::PTDFDCPowerFlow`:       use vPTDFDCPowerFlow() to store the Virtual PTDF matrix as       power*network*matrix and the ABA matrix as aux*network*matrix.
  * `sys::PSY.System`:       container storing the system data to consider in the PowerFlowData       structure.
  * `time_steps::Int`:       number of time periods to consider in the PowerFlowData structure. It       defines the number of columns of the matrices used to store data.       Default value = 1.
  * `timestep_names::Vector{String}`:       names of the time periods defines by the argmunet "time_steps". Default       value = String[].
