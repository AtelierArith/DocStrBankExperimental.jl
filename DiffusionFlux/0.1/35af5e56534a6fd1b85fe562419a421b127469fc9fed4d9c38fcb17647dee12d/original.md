Function to calculate the diffusion fluxes in Kg/m^2-s using Ficks law. The fluxes are corrected to  ensure that the sum is zero 

# Usage

flux_ficks!(jks::Array{T}, Dkm::Array{T} ,C1::Array{T}, C2::Array{T}, δ::T)

  * jks : vector of fluxes
  * C1 : concentration vector
  * C2 : concentration vector
  * δ  : distance between the cell centers
