`GradientVariablesPrimitive` と `GradientVariablesEntropy` は `CompressibleNavierStokesDiffusion1D` の勾配変数型パラメータです。デフォルトでは、勾配変数は `GradientVariablesPrimitive` に設定されています。代わりに `GradientVariablesEntropy` を指定すると、次の文献からエントロピー変数の定式化が使用されます。

  * Hughes, Mallet, Franca (1986) A new finite element formulation for computational fluid dynamics: I. Symmetric forms of the compressible Euler and Navier-Stokes equations and the second law of thermodynamics. [https://doi.org/10.1016/0045-7825(86)90127-1](https://doi.org/10.1016/0045-7825(86)90127-1)

`GradientVariablesEntropy` の下では、ナビエ-ストークスの離散化は証明可能なエントロピー安定性を持っています。
