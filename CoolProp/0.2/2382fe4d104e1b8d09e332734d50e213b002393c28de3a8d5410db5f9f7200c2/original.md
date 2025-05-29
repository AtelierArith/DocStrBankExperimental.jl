```
AbstractState_get_phase_envelope_data(handle::Clong, length::Integer, T::Array{Float64}, p::Array{Float64}, rhomolar_vap::Array{Float64}, rhomolar_liq::Array{Float64}, x::Array{Float64}, y::Array{Float64})
```

Get data from the phase envelope for the given mixture composition.

# Arguments

  * `handle`: The integer handle for the state class stored in memory
  * `length`: The number of elements stored in the arrays (both inputs and outputs MUST be the same length)
  * `T`: The pointer to the array of temperature (K)
  * `p`: The pointer to the array of pressure (Pa)
  * `rhomolar_vap`: The pointer to the array of molar density for vapor phase (m^3/mol)
  * `rhomolar_liq`: The pointer to the array of molar density for liquid phase (m^3/mol)
  * `x`: The compositions of the "liquid" phase (WARNING: buffer should be Ncomp*Npoints in length, at a minimum, but there is no way to check buffer length at runtime)
  * `y`: The compositions of the "vapor" phase (WARNING: buffer should be Ncomp*Npoints in length, at a minimum, but there is no way to check buffer length at runtime)

# Example

```julia
julia> HEOS=AbstractState_factory("HEOS","Methane&Ethane");
julia> length=200;
julia> t=zeros(length);p=zeros(length);x=zeros(2*length);y=zeros(2*length);rhomolar_vap=zeros(length);rhomolar_liq=zeros(length);
julia> AbstractState_set_fractions(HEOS, [0.2, 1 - 0.2])
julia> AbstractState_build_phase_envelope(HEOS, "none")
julia> AbstractState_get_phase_envelope_data(HEOS, length, t, p, rhomolar_vap, rhomolar_liq, x, y)
julia> AbstractState_free(HEOS)
```

# Note

If there is an error in an update call for one of the inputs, no change in the output array will be made

# Ref

CoolProp::AbstractState*get*phase*envelope*data(const long handle, const long length, double* T, double* p, double* rhomolar*vap, double* rhomolar*liq, double* x, double* y, long* errcode, char* message*buffer, const long buffer*length);
