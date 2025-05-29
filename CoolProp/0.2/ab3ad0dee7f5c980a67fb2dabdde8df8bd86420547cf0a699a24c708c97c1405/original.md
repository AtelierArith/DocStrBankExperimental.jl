```
AbstractState_update_and_common_out(handle::Clong, input_pair::Clong, value1::Array{Float64}, value2::Array{Float64}, length::Integer, T::Array{Float64}, p::Array{Float64}, rhomolar::Array{Float64}, hmolar::Array{Float64}, smolar::Array{Float64})
AbstractState_update_and_common_out(handle::Clong, input_pair::AbstractString, value1::Array{Float64}, value2::Array{Float64}, length::Integer, T::Array{Float64}, p::Array{Float64}, rhomolar::Array{Float64}, hmolar::Array{Float64}, smolar::Array{Float64})
```

Update the state of the AbstractState and get an output value five common outputs (temperature, pressure, molar density, molar enthalpy and molar entropy) from the AbstractState using pointers as inputs and output to allow array computation.

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `input_pair::Clong`: The integer value for the input pair obtained from get*input*pair_index
  * `input_pair::AbstractString`:
  * `value1`: The pointer to the array of the first input parameters
  * `value2`: The pointer to the array of the second input parameters
  * `length`: The number of elements stored in the arrays (both inputs and outputs MUST be the same length)
  * `T`: The pointer to the array of temperature
  * `p`: The pointer to the array of pressure
  * `rhomolar`: Array of molar density
  * `hmolar`: The array of molar enthalpy
  * `smolar`: Trray of molar entropy

# Example

```julia
julia> handle = AbstractState_factory("HEOS", "Water&Ethanol");
julia> pq_inputs = get_input_pair_index("PQ_INPUTS");
julia> AbstractState_set_fractions(handle, [0.4, 0.6]);
julia> T = [0.0]; p = [0.0]; rhomolar = [0.0]; hmolar = [0.0]; smolar = [0.0];
julia> AbstractState_update_and_common_out(handle, pq_inputs, [101325.0], [0.0], 1, T, p, rhomolar, hmolar, smolar);
julia> AbstractState_free(handle);
```
