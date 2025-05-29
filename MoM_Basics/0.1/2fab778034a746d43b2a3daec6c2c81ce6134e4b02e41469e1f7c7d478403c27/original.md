```
modiSimulationParams!(;ieT::Symbol=SimulationParams.ieT, 
meshfilename::String = SimulationParams.meshfilename, 
meshunit = SimulationParams.meshunit,
SHOWIMAGE = SimulationParams.SHOWIMAGE,
discreteVar = SimulationParams.discreteVar
)
```

ieT         ::Symbol, 积分方程类型，包括 EFIE, MFIE, CFIE等
