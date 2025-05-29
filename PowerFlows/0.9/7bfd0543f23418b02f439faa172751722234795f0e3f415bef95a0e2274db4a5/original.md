Evaluates the power flows on each system's branch by means of the Virtual PTDF matrix. Updates the PowerFlowData structure "data" and returns a dictionary containing a number of DataFrames equal to the numeber of timestep considered in "data". The DataFrame containts the flows and angles related to the information stored in the PSY.System considered as input.

# Arguments:

  * `::vPTDFDCPowerFlow`:       use vPTDFDCPowerFlow() to evaluate the power flows according to the       method based on the Virtual PTDF matrix
  * `sys::PSY.System`:       container gathering the system data used for the evaluation of flows       and angles.
