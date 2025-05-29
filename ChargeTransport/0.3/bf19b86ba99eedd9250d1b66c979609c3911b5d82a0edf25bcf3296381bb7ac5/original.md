```julia
mutable struct ParamsNodal
```

A struct holding the physical nodal, i.e. space-dependent parameters for a drift-diffusion simulation of a semiconductor device.

  * `dielectricConstant::Vector{Float64}`: A node dependent dielectric constant.

  * `doping::Vector{Float64}`: A 1D array with the corresponding doping values on each node.

  * `mobility::Matrix{Float64}`: A 2D array with the corresponding mobility values $\mu_\alpha$ for each carrier $\alpha$ on each node.

  * `densityOfStates::Matrix{Float64}`: A 2D array with the corresponding effective density of states values $N_\alpha$ for each carrier $\alpha$ on each node.

  * `bandEdgeEnergy::Matrix{Float64}`: A 2D array with the corresponding band-edge energy values $E_\alpha$ for each carrier $\alpha$ on each node.
