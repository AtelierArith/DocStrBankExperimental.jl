readBattMoJsonInputFile(inputFileName::String)

Reads the input file in JSON format and returns the input parameters as a dictionary

# Arguments

  * `inputFileName ::String` : name of the json file that contains the input

# Returns

An instance of [`InputParams`](@ref) that can be sent to the simulator via [`run_battery`](@ref)
