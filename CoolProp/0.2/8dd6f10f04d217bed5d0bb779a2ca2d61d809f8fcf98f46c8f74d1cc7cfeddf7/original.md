```
abstractState_all_critical_points(handle::Clong, length::Integer, T::Array{Float64}, p::Array{Float64}, rhomolar::Array{Float64}, stable::Array{Clong})
```

Calculate all the critical points for a given composition.

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `length`: The length of the buffers passed to this function
  * `T`: The pointer to the array of temperature (K)
  * `p`: The pointer to the array of pressure (Pa)
  * `rhomolar`: The pointer to the array of molar density (m^3/mol)
  * `stable`: The pointer to the array of boolean flags for whether the critical point is stable (1) or unstable (0)

# Note

If there is an error in an update call for one of the inputs, no change in the output array will be made

# Ref

CoolProp::AbstractState*all*critical*points(const long handle, const long length, double* T, double* p, double* rhomolar, long* stable, long* errcode, char* message*buffer, const long buffer_length);
