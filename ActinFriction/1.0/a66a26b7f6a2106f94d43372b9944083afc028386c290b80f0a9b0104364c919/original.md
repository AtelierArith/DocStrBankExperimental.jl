  * `k01::Float64`: Per site rate constant of initial crosslinker binding (s^-1)
  * `r01::Float64`: Per site rate of initial crosslinker binding (M^-1 s^-1)
  * `r10::Float64`: Per site rate (constant) of singly bound crosslinker unbinding (s^-1)
  * `r12::Float64`: Per site rate (constant) of singly bound crosslinker doubly binding (s^-1)
  * `r21::Float64`: Per site rate (constant) of doubly bound crosslinker unbinding one head (s^-1)
  * `deltas::Float64`: Spacing between binding sites on a filament (m)
  * `deltad::Float64`: Spacing for doubly bound crosslinkers (m)
  * `k::Float64`: Spring constant of crosslinker (N m^-1)
  * `T::Float64`: Temperature (K)
  * `Nf::Int64`: Number of filaments
  * `Nsca::Int64`: Number of scaffold filaments
  * `EI::Float64`:  Bending rigidity (N m^2)
  * `Lf::Float64`: Filament length (m)
  * `r0::Float64`: Jump rate prefactor
  * `Df::Float64`: Actin filament diameter (m)
  * `eta::Float64`: Viscosity of fluid (kg m^-1 s^-1)
  * `Ds::Float64`: Diffusion coefficient of singly bound crosslinkers on filament (m^2 s^-1)
  * `KsD::Float64`: Dissociation constant for single crosslinker binding from solution (M)
  * `KdD::Float64`: Dissociation constant for double crosslinker binding from solution (M)
  * `cX::Float64`: Crosslinker concentration (M)
  * `n::Float64`: Number of overlaps moving collectively during constriction
  * `tend::Float64`: Duration of dynamics (s)
  * `lambda0::Float64`: Initial lambda
  * `Ndtot0::Float64`: Initial total doubly-bound crosslinkers
  * `interval::Float64`: Write inteval for mean and variance of stochastic simulations
  * `zeta::Float64`: Friction coefficient

Parameters for actin-anillin ring system.
