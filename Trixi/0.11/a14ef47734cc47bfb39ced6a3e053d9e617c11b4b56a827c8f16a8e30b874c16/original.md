`GradientVariablesPrimitive` and `GradientVariablesEntropy` are gradient variable type parameters for `CompressibleNavierStokesDiffusion1D`. By default, the gradient variables are set to be `GradientVariablesPrimitive`. Specifying `GradientVariablesEntropy` instead uses the entropy variable formulation from

  * Hughes, Mallet, Franca (1986) A new finite element formulation for computational fluid dynamics: I. Symmetric forms of the compressible Euler and Navier-Stokes equations and the second law of thermodynamics. [https://doi.org/10.1016/0045-7825(86)90127-1](https://doi.org/10.1016/0045-7825(86)90127-1)

Under `GradientVariablesEntropy`, the Navier-Stokes discretization is provably entropy stable.
