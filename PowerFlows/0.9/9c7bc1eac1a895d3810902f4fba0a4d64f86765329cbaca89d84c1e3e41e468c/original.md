Evaluates the power flows on each system's branch by means of the PTDF matrix. Updates the PowerFlowData structure and returns a dictionary containing a DataFrame for the single timestep considered. The DataFrame containts the flows and angles related to the information stored in the PSY.System considered as input.

# Arguments:

  * `::PTDFDCPowerFlow`:       use PTDFDCPowerFlow() to evaluate the power flows according to the       method based on the PTDF matrix
  * `sys::PSY.System`:       container gathering the system data used for the evaluation of flows       and angles.
