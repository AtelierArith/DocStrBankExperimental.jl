```
SimulatorODEForwardSolver{algType,uType,tType,iip,integratorType<:AbstractODEIntegrator{algType,iip,uType,tType}} <: AbstractODEIntegrator{algType,iip,uType,tType}
```

SciML ODE インテグレーターをラップし、各観測可能なサンプルポイントがヒットするようにステッピング手順を制御する専門のインテグレータータイプです。
