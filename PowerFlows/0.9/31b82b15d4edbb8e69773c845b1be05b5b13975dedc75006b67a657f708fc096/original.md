Returns a dictionary containing the DC power flow results. Each key conresponds to the name of the considered time periods, storing a DataFrame with the PF results.

# Arguments:

  * `data::Union{PTDFPowerFlowData, vPTDFPowerFlowData, ABAPowerFlowData}`:       PowerFlowData strcuture containing power flows and bus angles.
  * `sys::PSY.System`:       container storing the systam information.
