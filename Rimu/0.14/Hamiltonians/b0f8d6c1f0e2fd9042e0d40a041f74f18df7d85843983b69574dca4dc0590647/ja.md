モジュール `Rimu.Hamiltonians` は、ハミルトニアンを扱うための型と関数を定義しています。

## エクスポートされた具体的なハミルトニアン型

実空間ハバードモデル

  * [`HubbardReal1D`](@ref)
  * [`HubbardReal1DEP`](@ref)
  * [`HubbardRealSpace`](@ref)
  * [`ExtendedHubbardReal1D`](@ref)

運動量空間ハバードモデル

  * [`HubbardMom1D`](@ref)
  * [`HubbardMom1DEP`](@ref)

調和振動子モデル

  * [`HOCartesianContactInteractions`](@ref)
  * [`HOCartesianEnergyConservedPerDim`](@ref)
  * [`HOCartesianCentralImpurity`](@ref)

その他

  * [`FroehlichPolaron`](@ref)
  * [`MatrixHamiltonian`](@ref)
  * [`Transcorrelated1D`](@ref)

## [ラッパー](#Hamiltonian-wrappers)

  * [`GutzwillerSampling`](@ref)
  * [`GuidingVectorSampling`](@ref)
  * [`ParitySymmetry`](@ref)
  * [`TimeReversalSymmetry`](@ref)
  * [`Stoquastic`](@ref)

## [観測量](#Observables)

  * [`ParticleNumberOperator`](@ref)
  * [`G2RealCorrelator`](@ref)
  * [`G2MomCorrelator`](@ref)
  * [`G2RealSpace`](@ref)
  * [`DensityMatrixDiagonal`](@ref)
  * [`SingleParticleExcitation`](@ref)
  * [`TwoParticleExcitation`](@ref)
  * [`Momentum`](@ref)
  * [`AxialAngularMomentumHO`](@ref)

## [ハミルトニアンを扱うためのインターフェース](#Hamiltonians-interface)

  * [`AbstractHamiltonian`](@ref): モジュール [`Interfaces`](@ref) で定義されています。
