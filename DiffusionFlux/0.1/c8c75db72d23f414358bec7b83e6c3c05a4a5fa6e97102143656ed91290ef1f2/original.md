Function to calculate binary diffusion coeffcients and Knudsen diffusion coeffcients, which are required for the evaluation of DGM fluxes

# Usage

effective*coefficients!(dgm*obj::WorkSpace, pm::Properties, sp_trd, p::Float64, T::Float64 ,molwts::Array{Float64})

  * dgm_obj : A struct of the type WorkSpace which stores the diffusion coeffcients matrix
  * pm : Porous media properties (struct of the type Properties)
  * sp*trd : Array of Species transport data, which is obtained by calling create*transport_data of TransportProperties
  * p : pressure in (Pa)
  * T : Temperature (K)
  * molwts : molecular weights vector
