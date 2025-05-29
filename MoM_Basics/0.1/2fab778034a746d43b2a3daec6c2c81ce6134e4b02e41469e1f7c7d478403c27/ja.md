```
modiSimulationParams!(;ieT::Symbol=SimulationParams.ieT, 
meshfilename::String = SimulationParams.meshfilename, 
meshunit = SimulationParams.meshunit,
SHOWIMAGE = SimulationParams.SHOWIMAGE,
discreteVar = SimulationParams.discreteVar
)
```

ieT         ::Symbol, 積分方程の種類、EFIE、MFIE、CFIEなどを含む
