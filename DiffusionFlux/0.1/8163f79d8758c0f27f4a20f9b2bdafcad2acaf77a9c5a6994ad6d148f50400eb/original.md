Function to calcuate the mass flux (kg/m^2-s) at the inteface between flow channel and porous media. The pressure driven flux is assumed to be negligible at the inteface 

# Usage

interface*flux!(jks::Array{T,1},C*ch, C*pm, dgm*obj::WorkSpace, molwts::Array{T}, Temp::T, δ::T)

  * jks : Storage for species flux (1D Array)
  * C_ch : concentration in the flow channel
  * C_pm : concentration in the porous media
  * dgm_obj : Diffusion matrix for DGM flux calculations
  * molwts  : vector of molecular weights
  * Temp : Temperature (K)
  * δ   : distance between the cell centers
