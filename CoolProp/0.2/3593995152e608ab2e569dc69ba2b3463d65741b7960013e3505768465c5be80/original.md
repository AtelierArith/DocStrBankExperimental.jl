```
AbstractState_update_and_5_out(handle::Clong, input_pair::Clong, value1::Array{Float64}, value2::Array{Float64}, length::Integer, outputs::Array{Clong}, out1::Array{Float64}, out2::Array{Float64}, out3::Array{Float64}, out4::Array{Float64}, out5::Array{Float64})
AbstractState_update_and_5_out{S<:AbstractString}(handle::Clong, input_pair::AbstractString, value1::Array{Float64}, value2::Array{Float64}, length::Integer, outputs::Array{S}, out1::Array{Float64}, out2::Array{Float64}, out3::Array{Float64}, out4::Array{Float64}, out5::Array{Float64})
```

Update the state of the AbstractState and get an output value five common outputs (temperature, pressure, molar density, molar enthalpy and molar entropy) from the AbstractState using pointers as inputs and output to allow array computation.

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `input_pair::Clong`: The integer value for the input pair obtained from get*input*pair_index
  * `input_pair::AbstractString`:
  * `value1`: The pointer to the array of the first input parameters
  * `value2`: The pointer to the array of the second input parameters
  * `length`: The number of elements stored in the arrays (both inputs and outputs MUST be the same length)
  * `outputs`: The 5-element vector of indices for the outputs desired
  * `out1`: The array for the first output
  * `out2`: The array for the second output
  * `out3`: The array for the third output
  * `out4`: The array for the fourth output
  * `out5`: The array for the fifth output
