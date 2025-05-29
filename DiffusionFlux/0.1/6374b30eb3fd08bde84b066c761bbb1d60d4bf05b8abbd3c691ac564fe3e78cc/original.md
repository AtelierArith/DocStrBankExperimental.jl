Function to calculate the mass fluxes (kg/m^2-s) at the interface between two cells using modified Fickian model  The fluxes at the boundary cells are not evaluated in this function. If There are n cells, there will be n-1 internal cell faces 

# Usage

flux*porous*media*fick!(jks::Array{Array{T,1},1}, C::Array{Array{T,1},1}, pm::Properties, sp*tr_data, ws::WorkSpace , molwts::Array{T}, Temp::T, δ::T)

  * jks : vector{vector} for storing the fluxes jks[n] stands for the flux at the interface between n and (n+1)th cell
  * C : vector{vector} concentrations in all cells
  * pm : Porous media properties (struct of the type Properties)
  * sp*tr*data : Array of Species transport data, which is obtained by calling create*transport*data of TransportProperties
  * ws : A struct of the type WorkSpace which stores the diffusion coeffcients matrix
  * molwts : vector of molecular weights
  * Temp : Temperature (K)
  * δ : distance between cell centers
