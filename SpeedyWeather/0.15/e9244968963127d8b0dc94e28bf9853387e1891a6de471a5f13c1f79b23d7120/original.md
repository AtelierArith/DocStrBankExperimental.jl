Struct that holds various precomputed arrays for the semi-implicit correction to prevent gravity waves from amplifying in the primitive equation model.

  * `trunc::Int64`: spectral resolution
  * `nlayers::Int64`: number of vertical layers
  * `α::Any`: time-step coefficient: 0=explicit, 0.5=centred implicit, 1=backward implicit
  * `temp_profile::Any`: vertical temperature profile, obtained from diagn on first time step
  * `ξ::Base.RefValue`: time step 2α*Δt packed in RefValue for mutability
  * `R::Any`: divergence: operator for the geopotential calculation
  * `U::Any`: divergence: the -RdTₖ∇² term excl the eigenvalues from ∇² for divergence
  * `L::Any`: temperature: operator for the TₖD + κTₖDlnps/Dt term
  * `W::Any`: pressure: vertical averaging of the -D̄ term in the log surface pres equation
  * `L0::Any`: components to construct L, 1/ 2Δσ
  * `L1::Any`: vert advection term in the temperature equation (below+above)
  * `L2::Any`: factor in front of the div*sum*above term
  * `L3::Any`: *sum*above operator itself
  * `L4::Any`: factor in front of div term in Dlnps/Dt
  * `S::Any`: for every l the matrix to be inverted
  * `S⁻¹::Any`: combined inverted operator: S = 1 - ξ²(RL + UW)
