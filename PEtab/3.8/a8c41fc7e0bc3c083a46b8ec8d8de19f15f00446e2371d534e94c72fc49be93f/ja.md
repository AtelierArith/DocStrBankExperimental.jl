PEtabLogDensity(prob::PEtabODEProblem)

`prob`から事後分布と勾配関数を使用して`LogDensityProblem`を作成します。

この[`LogDensityProblem`インターフェース](https://github.com/tpapp/LogDensityProblems.jl)は、`AdvancedHMC.jl`（`Turing.jl`で使用されるNUTSのようなアルゴリズムを含む）や`AdaptiveMCMC.jl`などのパッケージを使用してベイズ推論を行うために必要なすべてを定義します。
