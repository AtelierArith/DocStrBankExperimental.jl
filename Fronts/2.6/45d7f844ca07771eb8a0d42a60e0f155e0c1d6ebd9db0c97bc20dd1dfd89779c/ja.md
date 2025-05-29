```
boltzmann(prob::CauchyProblem) -> DifferentialEquations.ODEProblem
boltzmann(prob::SorptivityCauchyProblem) -> DifferentialEquations.ODEProblem
```

`prob`をボルツマン変数`o`に関するODE問題に変換します。

ODE問題は、定常状態に達したときに自動的に終了するように設定されています（`.retcode == ReturnCode.Success`）。

参照: [`DifferentialEquations`](https://diffeq.sciml.ai/stable/)
