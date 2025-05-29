The module `Rimu.Hamiltonians` defines types and functions for working with Hamiltonians.

## Exported concrete Hamiltonian types

Real space Hubbard models

  * [`HubbardReal1D`](@ref)
  * [`HubbardReal1DEP`](@ref)
  * [`HubbardRealSpace`](@ref)
  * [`ExtendedHubbardReal1D`](@ref)

Momentum space Hubbard models

  * [`HubbardMom1D`](@ref)
  * [`HubbardMom1DEP`](@ref)

Harmonic oscillator models

  * [`HOCartesianContactInteractions`](@ref)
  * [`HOCartesianEnergyConservedPerDim`](@ref)
  * [`HOCartesianCentralImpurity`](@ref)

Other

  * [`FroehlichPolaron`](@ref)
  * [`MatrixHamiltonian`](@ref)
  * [`Transcorrelated1D`](@ref)

## [Wrappers](#Hamiltonian-wrappers)

  * [`GutzwillerSampling`](@ref)
  * [`GuidingVectorSampling`](@ref)
  * [`ParitySymmetry`](@ref)
  * [`TimeReversalSymmetry`](@ref)
  * [`Stoquastic`](@ref)

## [Observables](#Observables)

  * [`ParticleNumberOperator`](@ref)
  * [`G2RealCorrelator`](@ref)
  * [`G2MomCorrelator`](@ref)
  * [`G2RealSpace`](@ref)
  * [`DensityMatrixDiagonal`](@ref)
  * [`SingleParticleExcitation`](@ref)
  * [`TwoParticleExcitation`](@ref)
  * [`Momentum`](@ref)
  * [`AxialAngularMomentumHO`](@ref)

## [Interface for working with Hamiltonians](#Hamiltonians-interface)

  * [`AbstractHamiltonian`](@ref): defined in the module [`Interfaces`](@ref)
