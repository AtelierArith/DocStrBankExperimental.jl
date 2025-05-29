readBattMoMatlabInputFile(inputFileName::String)

Reads the input from a matlab output file which contains a description of the model and returns an `MatlabInputParams` that can be sent to the simulator.

# Arguments

  * `inputFileName ::String` : filename of the input

# Returns

An instance of [`MatlabInputParams`](@ref) that can be sent to the simulator via [`run_battery`](@ref)
