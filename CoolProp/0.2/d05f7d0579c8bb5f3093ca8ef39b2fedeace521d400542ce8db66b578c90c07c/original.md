```
AbstractState_get_spinodal_data(handle::Clong, length::Integer, tau::Array{Float64}, dalta::Array{Float64}, m1::Array{Float64})
```

Get data for the spinodal curve.

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `length`: The number of elements stored in the arrays (all outputs MUST be the same length)
  * `tau`: The pointer to the array of reciprocal reduced temperature
  * `delta`: The pointer to the array of reduced density
  * `m1`: The pointer to the array of M1 values (when L1=M1=0, critical point)

# Note

If there is an error, no change in the output arrays will be made

# Example

julia> HEOS=AbstractState*factory("HEOS","Methane&Ethane"); julia> AbstractState*set*fractions(HEOS, [0.1, 0.9]); julia> AbstractState*build*spinodal(HEOS); julia> tau, delta, m1 = AbstractState*get*spinodal*data(HEOS, 127);

# Ref

CoolProp::AbstractState*get*spinodal*data(const long handle, const long length, double* tau, double* delta, double* M1, long* errcode, char* message*buffer, const long buffer_length);
