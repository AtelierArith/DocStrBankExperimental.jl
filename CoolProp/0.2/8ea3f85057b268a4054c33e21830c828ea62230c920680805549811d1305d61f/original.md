```
AbstractState_update_and_1_out(handle::Clong, input_pair::Clong, value1::Array{Float64}, value2::Array{Float64}, length::Integer, output::Clong, out::Array{Float64})
AbstractState_update_and_1_out(handle::Clong, input_pair::AbstractString, value1::Array{Float64}, value2::Array{Float64}, length::Integer, output::AbstractString, out::Array{Float64})
```

Update the state of the AbstractState and get one output value (temperature, pressure, molar density, molar enthalpy and molar entropy) from the AbstractState using pointers as inputs and output to allow array computation.

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `input_pair::Clong`: The integer value for the input pair obtained from get*input*pair_index
  * `input_pair::AbstractString`:
  * `value1`: The pointer to the array of the first input parameters
  * `value2`: The pointer to the array of the second input parameters
  * `length`: The number of elements stored in the arrays (both inputs and outputs MUST be the same length)
  * `output`: The indice for the output desired
  * `out`: The array for output
