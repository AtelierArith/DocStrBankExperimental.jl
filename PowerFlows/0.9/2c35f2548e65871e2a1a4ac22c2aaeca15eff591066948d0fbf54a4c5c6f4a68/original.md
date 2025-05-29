Evaluates the power flows on each system's branch by means of the PTDF matrix. Updates the PowerFlowData structure "data" and returns a dictionary containing a number of DataFrames equal to the numeber of timestep considered in "data". Each DataFrame containts the flows and angles.

# Arguments:

  * `data::PTDFPowerFlowData`:       PowerFlowData structure containing the system's data per each timestep       considered, as well as the PTDF matrix.
  * `sys::PSY.System`:       container gathering the system data.
