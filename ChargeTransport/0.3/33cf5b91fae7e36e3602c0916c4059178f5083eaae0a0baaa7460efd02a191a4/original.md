```julia
mutable struct Params
```

A struct holding the physical region dependent parameters for a drift-diffusion simulation of a semiconductor device.

  * `numberOfNodes::Int64`: Number of nodes used for the disretization of the domain $\mathbf{\Omega}$.

  * `numberOfRegions::Int64`: Number of subregions $\mathbf{\Omega}_k$ within the domain $\mathbf{\Omega}$.

  * `numberOfBoundaryRegions::Int64`: Number of boundary regions $(\partial \mathbf{\Omega})_k$ such that $\partial \mathbf{\Omega} = \cup_k (\partial \mathbf{\Omega})_k$. Note that here are inner and outer boundaries calculated.

  * `numberOfCarriers::Int64`: Number of moving charge carriers.

  * `invertedIllumination::Int64`: Parameter for the direction of illumination. If illumination is coming from the left, then set this value to 1. Otherwise, if the illumination comes from the right, set this value to -1.

  * `temperature::Float64`: A given constant temperature.

  * `UT::Float64`: The thermal voltage, which reads  $U_T = k_B T / q$.

  * `γ::Float64`: The parameter of the Blakemore statistics (needed for the generalizedSG flux).

  * `r0::Float64`: Prefactor of electro-chemical reaction of internal boundary conditions.

  * `prefactor_SRH::Float64`: Prefactor for stationary SRH recombination.

  * `generationPeak::Float64`: Parameter for the shift of generation peak of the Beer-Lambert generation profile.

  * `SchottkyBarrier::Vector{Float64}`: An array for the given Schottky barriers at present Schotkky contacts.

  * `contactVoltage::Vector{Float64}`: An array containing a constant value for the applied voltage.

  * `bψEQ::Vector{Float64}`: An array containing a constant value for the electric potential in case of Dirichlet boundary conditions.

  * `chargeNumbers::Vector{Float64}`: An array with the corresponding charge numbers $z_\alpha$ for all carriers $\alpha$.

  * `bBandEdgeEnergy::Matrix{Float64}`: An array with the corresponding boundary band-edge energy values $E_\alpha$ in each region for each carrier $\alpha$.

  * `bDensityOfStates::Matrix{Float64}`: An array with the corresponding boundary effective density of states values $N_\alpha$ for each carrier $\alpha$.

  * `bMobility::Matrix{Float64}`: A 2D array with the corresponding boundary mobility values $\mu_\alpha$ in each boundary region for each carrier $\alpha$.

  * `bDoping::Matrix{Float64}`: A 2D array with the corresponding boundary doping values for each carrier $\alpha$.

  * `bVelocity::Matrix{Float64}`: A 2D array with the corresponding boundary velocity values for each carrier $\alpha$, when assuming Schottky contacts.

  * `bReactionCoefficient::Matrix{Float64}`: An array to define the reaction coefficient at internal boundaries.

  * `recombinationSRHvelocity::Matrix{Float64}`: A 2D array with the corresponding recombination surface boundary velocity values for electrons and holes.

  * `bRecombinationSRHTrapDensity::Matrix{Float64}`: A 2D array with the corresponding recombination surface boundary density values for electrons and holes.

  * `bRecombinationSRHLifetime::Matrix{Float64}`: A 2D array with the corresponding recombination surface recombination velocities.

  * `bDensityEQ::Matrix{Float64}`: A 2D array containing the equilibrium density of electric charge carriers at the boundary.

  * `doping::Matrix{Float64}`: A 2D array with the corresponding doping values for each carrier $\alpha$ on each region.

  * `densityOfStates::Matrix{Float64}`: A 2D array with the corresponding effective density of states values $N_\alpha$ for each carrier $\alpha$ on each region.

  * `bandEdgeEnergy::Matrix{Float64}`: A 2D array with the corresponding band-edge energy values $E_\alpha$ for each carrier $\alpha$ on each region.

  * `mobility::Matrix{Float64}`: A 2D array with the corresponding mobility values $\mu_\alpha$ for each carrier $\alpha$ on each region.

  * `recombinationSRHLifetime::Matrix{Float64}`: A 2D array with the corresponding SRH lifetimes $\tau_n, \tau_p$ for electrons and holes.

  * `recombinationSRHTrapDensity::Matrix{Float64}`: A 2D array with the corresponding time-independent SRH trap densities $n_{\tau}, p_{\tau}$ for electrons and holes.

  * `recombinationAuger::Matrix{Float64}`: A 2D array with the corresponding Auger coefficients for electrons and holes.

  * `dielectricConstant::Vector{Float64}`: A region dependent dielectric constant.

  * `dielectricConstantImageForce::Vector{Float64}`: A region dependent image force dielectric constant.

  * `generationIncidentPhotonFlux::Vector{Float64}`: A region dependent array for the prefactor in the generation process which is the incident photon flux.

  * `generationUniform::Vector{Float64}`: A region dependent array for an uniform generation rate.

  * `generationAbsorption::Vector{Float64}`: A region dependent array for the absorption coefficient in the generation process.

  * `recombinationRadiative::Vector{Float64}`: A region dependent array for the radiative recombination rate.
