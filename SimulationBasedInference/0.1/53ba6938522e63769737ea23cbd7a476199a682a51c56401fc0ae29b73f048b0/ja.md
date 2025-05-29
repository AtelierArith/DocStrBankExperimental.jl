```
SimulatorInferenceProblem{
    modelPriorType<:AbstractSimulatorPrior,
    uType,
    fwdProbType<:SimulatorForwardProblem,
    fwdSolverType,
    priorType<:JointPrior
} <: SciMLBase.AbstractSciMLProblem
```

観測データに基づいてモデルパラメータの事後分布を求めるための一般的なシミュレーションベースのベイズ推定問題を表します。
